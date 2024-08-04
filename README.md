# hello-world

# Hello World App

This is a simple Flask-based "Hello World" application that is containerized using Docker. The project demonstrates how to build, deploy, and manage a Docker container on an AWS EC2 instance using Terraform and GitHub Actions.

## Table of Contents

- [Project Overview](#project-overview)
- [Setup and Installation](#setup-and-installation)
  - [Prerequisites](#prerequisites)
  - [Local Setup](#local-setup)
  - [Docker Setup](#docker-setup)
  - [AWS EC2 Setup](#aws-ec2-setup)
- [CI/CD Pipeline](#cicd-pipeline)
- [Contributing](#contributing)
- [License](#license)

## Project Overview

This project is a simple web application that returns "Hello, World!" when accessed. It is built using Flask and containerized using Docker. The application is deployed on an AWS EC2 instance using Terraform for infrastructure management and GitHub Actions for CI/CD.

## Setup and Installation

### Prerequisites

Before you begin, ensure you have the following installed on your local machine:

- Python 3.9
- Docker
- Terraform
- AWS CLI
- Git

### Local Setup

1. Clone the repository:

    ```sh
    git clone https://github.com/thenameisonkars/hello-world.git
    cd hello-world
    ```

2. Create and activate a virtual environment:

    ```sh
    python3 -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. Install the dependencies:

    ```sh
    pip install -r app/requirements.txt
    ```

4. Run the application:

    ```sh
    python app/app.py
    ```

5. Access the application in your browser at `http://localhost:5000`.

### Docker Setup

1. Build the Docker image:

    ```sh
    docker build -t your-dockerhub-username/hello-world .
    ```

2. Run the Docker container:

    ```sh
    docker run -d -p 5000:5000 your-dockerhub-username/hello-world
    ```

3. Access the application in your browser at `http://localhost:5000`.

### AWS EC2 Setup

1. Initialize Terraform:

    ```sh
    terraform init
    ```

2. Apply the Terraform configuration to create the EC2 instance:

    ```sh
    terraform apply
    ```

3. SSH into the EC2 instance and set up Docker:

    ```sh
    ssh -i path/to/your/key.pem ubuntu@your-ec2-public-dns
    ```

4. Run the Docker container on the EC2 instance:

    ```sh
    docker pull your-dockerhub-username/hello-world:latest
    docker run -d -p 5000:5000 your-dockerhub-username/hello-world:latest
    ```

5. Access the application in your browser using the EC2 instance's public DNS.

## CI/CD Pipeline

This project uses GitHub Actions to automate the build and deployment process. The workflow is defined in `.github/workflows/deploy.yml` and includes the following steps:

1. **Checkout code**: Retrieves the latest code from the repository.
2. **Build Docker image**: Builds the Docker image and tags it.
3. **Login to DockerHub**: Authenticates with DockerHub using secrets.
4. **Push Docker image**: Pushes the built image to DockerHub.
5. **Deploy to EC2**: SSHs into the EC2 instance, pulls the latest Docker image, and runs the container.

## Contributing

Contributions are welcome! Please fork this repository and submit pull requests with any improvements or bug fixes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
