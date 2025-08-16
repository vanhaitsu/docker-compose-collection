# Docker Compose Collection

A collection of ready-to-use **Docker Compose** configurations for popular databases or third-party services. Perfect for development, testing, or quickly spinning up local environments.

## Prerequisites

- Docker and Docker Compose.

## Usage

1. Clone the repository.
2. Go into the service folder you want to start, for example PostgreSQL.

```
cd PostgreSQL
```

3. Copy the environment template.

```
cp .env.example .env.local
```

4. Edit `.env.local` and `docker-compose.yml` if needed (username, password, ports, database name, etc.).
5. Start the service.

```
docker-compose --env-file .env.local up -d
```

6. Check running containers (optional).

```
docker ps
```

7. Connect to the service using the credentials from `.env.local`.

## Volumes & Data Persistence

Each service is configured with a **named Docker volume** for persistent storage.
Example from the Microsoft SQL Server setup:

```
services:
  mssql:
    ...
    volumes:
      - volume_name:/var/opt/mssql
volumes:
  volume_name:
```

## Stopping & Cleaning Up

- To stop and remove the containers.

```
docker-compose --env-file .env.local down
```

- To also remove volumes (reset data).

```
docker-compose --env-file .env.local down -v
```

## Configuration

- Default variables are in `.env.example`.
- Override them by editing `.env.local` (which is ignored by Git).

# Notes

- These configs are designed for **local development only**.
- Don’t expose them directly to the internet or production systems.
