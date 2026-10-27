# Dockerized Python API

A beginner-friendly Python REST API packaged with Docker. This project demonstrates API development, containerization, endpoint testing, and basic container troubleshooting.

## Project Overview

The application uses Flask to provide two HTTP endpoints. Docker packages the application and its Python dependencies into a reproducible container image.

## Tech Stack

- Python 3.10
- Flask
- Docker
- Linux / Ubuntu (WSL2)
- Git and GitHub

## API Endpoints

| Method | Endpoint | Description | Expected Response |
|---|---|---|---|
| GET | `/` | Returns application status | `{"message":"Dockerized Python API","status":"running"}` |
| GET | `/health` | Health check | `{"status":"ok"}` |

## Project Structure

```text
dockerized-python-api/
├── app.py
├── Dockerfile
├── requirements.txt
├── .gitignore
└── README.md
```

## Build the Docker Image

```bash
sudo docker build -t saalyk-python-api:1.0 .
```

## Run the Container

```bash
sudo docker run --rm -d --name python-api -p 5000:5000 saalyk-python-api:1.0
```

## Test the API

Check application status:

```bash
curl http://127.0.0.1:5000/
```

Check application health:

```bash
curl http://127.0.0.1:5000/health
```

## Troubleshooting

**Problem: Port 5000 is already in use**

Identify the process listening on the port:

```bash
sudo ss -ltnp 'sport = :5000'
```

Stop the existing application if appropriate, or choose a different host port.

**Problem: Container is not running**

Check running containers:

```bash
sudo docker ps
```

Inspect application logs:

```bash
sudo docker logs python-api
```

## Stop the Container

```bash
sudo docker stop python-api
```

The container is started with `--rm`, so Docker automatically removes it when it stops. The built image remains available locally.

## Limitations

- This is a learning project, not a production deployment.
- Flask's built-in development server is used; a production WSGI server and additional security hardening would be needed before production use.
- The project runs locally and does not require AWS resources.

## Skills Demonstrated

- Python API development
- REST endpoint testing with `curl`
- Docker image creation and container lifecycle management
- Port mapping and networking troubleshooting
- Application log inspection
- Linux command-line operations

## Author

GitHub: [saalyk](https://github.com/saalyk)
