# Toth Workflows

This repository is the central hub for our Continuous Integration and Continuous Deployment (CI/CD) workflows. These workflows are designed to automate the process of building, testing, and deploying our applications, ensuring a smooth and reliable delivery pipeline.

## Workflows Overview

In the realm of Toth, the god of wisdom, each script and action has its purpose. Here we maintain the arcane knowledge of automation that empowers our project's continuous evolution and delivery.

### 🐳 Docker Build and Publish (`docker-build-publish.yml`)

The `docker-build-publish.yml` workflow is responsible for packaging our services into Docker containers and pushing them to Amazon Elastic Container Registry (ECR). Here's how it works:

- **Trigger**: This workflow is triggered on call. Currently it is implemented in a way that it triggers when a new release is created.
- **Build**: It builds the Docker image using the Dockerfile located in the project's root directory.
- **Authenticate**: The workflow uses OpenID Connect (OIDC) to authenticate with AWS without the need to store sensitive credentials as secrets.
- **Push**: After successful authentication and build, it pushes the image to a specified ECR repository.

### 🌐 Publish Frontend (`publish-frontend.yml`)

Our `publish-frontend.yml` workflow is all about bringing our frontend to the spotlight:

- **Trigger**: Similar to the Docker workflow, it gets to work on releases.
- **Build**: The workflow runs the build process for our frontend, utilizing static site generation.
- **Authenticate**: Utilizes OIDC for AWS authentication, ensuring a secure pipeline without hard-coded secrets.
- **Deploy**: Once the build artifacts are ready, it uploads it to S3 and replaces everything inside the bucket.
