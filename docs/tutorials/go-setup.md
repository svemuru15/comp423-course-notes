# Setting up a dev container for Go

* Primary author: [Sritan Vemuru](https://github.com/svemuru15)
* Reviewer: [Krish Singhvi](https://github.com/krishsinghvi)

## Introduction

This tutorial will help you setup a Go project that produces a "Hello, World!" program.

## Prerequisites

Install the following softwares:

* [VS Code](https://code.visualstudio.com/) with Dev Containers extension
* [Git](https://git-scm.com/)
* [Docker](https://www.docker.com/)

## Step 1: Create Github Reposity and Local Directory

1. Open terminal and run the following commands:
    
        mkdir hello-world-go

        cd hello-world-go

        git init

2. Create your Github Repository
    
    (1) Log in to your GitHub account and navigate to the Create a New Repository page.

    (2) Fill in the details as follows:

        Repository Name: hello-world-go
        Description: "Hello World Project in Go."
        Visibility: Public

    (3) Click Create Repository.

3. Connect your remote repository

    Add the Github repo using the below command in the terminal(replace your-username with your GitHub username):

        git remote add origin https://github.com/<your-username>/hello-world-go


## Step 2: Setup Dev Container

1. Create a .devcontainer directory and a devcontainer.json file using the below commands:

        mkdir .devcontainer

        touch .devcontainer/devcontainer.json

2. Add the following to your devcontainer.json file:

        {
        "name": "Go Dev Container",
        "image": "mcr.microsoft.com/devcontainers/go:1-1.22-bookworm",
        "customizations": {
            "vscode": {
            "settings": {},
            "extensions": ["golang.go"]
            }
        }
        }

3. Reopen the Project in a VSCode Dev Container

    Reopen the project in the container by pressing Ctrl+Shift+P (or Cmd+Shift+P on Mac), typing "Dev Containers: Reopen in Container," and selecting the option.

4. Verify that Go is installed in the container by running:

        go version


## Step 3: Create Go Project

1. Run the following commands in the dev container(replace your-username with your GitHub username):

        go mod init github.com/<yourusername>/go-hello-world

2. Create the main.go file:

        touch main.go

3. Paste the following code into your hello.go file and save the file:

        package main

        import "fmt"

        func main() {
            fmt.Println("Hello, World!")
        }

## Step 4: Compile and Run Go Project

1. Compile the project:

        go build main.go

2. Run the executable file:

        ./main

3. An alternative way to do this would be to use the run command which combines these 2 steps:

        go run main.go

The go run command compiles and executes the code immediately, but the compilation is not stored. This helps us as this makes sure less storage is used. The go build command compiles the code and creates a permanent binary file that can be run independently. In the same way as gcc, go build converts code into an executable file.

Step 6: Push changes to Github

1. Stages files:

        git add .

2. Commit changes:

        git commit -m "your message here"

3. Push to remote

        git push origin main