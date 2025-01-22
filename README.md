# Docker Compose Setup for PostgreSQL and CloudBeaver

This Docker Compose file provides a quick and convenient way to set up a local environment with PostgreSQL and CloudBeaver.

## Overview

The setup includes:

- **PostgreSQL**: A powerful, open-source object-relational database system.
- **CloudBeaver**: A web-based interface for managing databases, based on DBeaver.

## Features

- Easily configurable through environment variables.
- Persistent data storage using Docker volumes.
- Web-based database management with CloudBeaver.
- Fallback defaults for all environment variables to ensure seamless setup.

## Services

### PostgreSQL

- **Image**: `postgres:15`
- **Ports**: Exposed on `5432`
- **Environment Variables**:
  - `POSTGRES_USER` (default: `default_user`)
  - `POSTGRES_PASSWORD` (default: `default_password`)
  - `POSTGRES_DB` (default: `default_database`)

### CloudBeaver

- **Image**: `dbeaver/cloudbeaver:latest`
- **Ports**: Exposed on `8080`
- **Environment Variables**:
  - `CB_ADMIN_NAME` (default: `admin`)
  - `CB_ADMIN_PASSWORD` (default: `admin123`)
- **Dependencies**: Depends on the PostgreSQL service.

## Getting Started

### Prerequisites

- Docker and Docker Compose installed on your system.

### Steps to Run

1. Clone the repository or copy the `docker-compose.yml` and `.env` file to your local environment.
2. Customize the `.env` file as needed to set your own variables:
   ```env
   POSTGRES_USER=my_user
   POSTGRES_PASSWORD=my_password
   POSTGRES_DB=my_database
   CB_ADMIN_NAME=my_admin
   CB_ADMIN_PASSWORD=my_admin_password
   ```
3. Start the services using Docker Compose:
   ```bash
   docker-compose up -d
   ```
4. Access CloudBeaver in your browser at: [http://localhost:8080](http://localhost:8080).
5. Log in to CloudBeaver using the admin credentials:
   - **Username**: `CB_ADMIN_NAME` (or `admin` by default).
   - **Password**: `CB_ADMIN_PASSWORD` (or `admin123` by default).
6. Configure a new connection to PostgreSQL:
   - **Host**: `postgres`
   - **Port**: `5432`
   - **Database**: `POSTGRES_DB`
   - **Username**: `POSTGRES_USER`
   - **Password**: `POSTGRES_PASSWORD`

## Volumes

- `postgres_data`: Used to persist PostgreSQL data locally, ensuring data is retained across container restarts.

## Environment Variables

| Variable            | Description                | Default Value      |
| ------------------- | -------------------------- | ------------------ |
| `POSTGRES_USER`     | PostgreSQL username        | `default_user`     |
| `POSTGRES_PASSWORD` | PostgreSQL password        | `default_password` |
| `POSTGRES_DB`       | PostgreSQL database name   | `default_database` |
| `CB_ADMIN_NAME`     | CloudBeaver admin username | `admin`            |
| `CB_ADMIN_PASSWORD` | CloudBeaver admin password | `admin123`         |

## Stopping the Services

To stop the services, run:

```bash
docker-compose down
```

## Logs

To view the logs of all services:

```bash
docker-compose logs -f
```
