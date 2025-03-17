# Qdrant Docker Setup

This project contains the Docker configuration to run Qdrant, a high-performance vector database.

## About Qdrant

Qdrant is an open-source vector database optimized for storing and searching high-dimensional vectors. It's particularly useful for:

- Recommendation systems
- Semantic search
- Similarity analysis
- AI/ML applications

## Requirements

- Docker
- Docker Compose

## Project Structure

```text
.
├── compose.yaml      # Docker Compose configuration
├── data/            # Directory for persistent storage
└── README.md        # This file
```

## Configuration

The project is configured with the following features:

### Ports

- HTTP: 6333
- gRPC: 6334

### Resources

- CPU Limit: 2 cores
- Memory Limit: 2GB
- Minimum CPU Reservation: 1 core
- Minimum Memory Reservation: 1GB

### Performance

- Search Threads: 4
- Indexing Threads: 4
- Open Files Limit: 65536

### Security

- No new privileges
- Dedicated network
- Healthcheck configured

## How to Use

1. Clone this repository:

```bash
git clone [REPOSITORY_URL]
cd qdrant-docker
```

2. Start the service:

```bash
docker compose up -d
```

3. Check the status:

```bash
docker compose ps
```

4. Access the HTTP interface:

```text
http://localhost:6333
```

## Main Endpoints

- Health Check: `http://localhost:6333/health`
- HTTP API: `http://localhost:6333`
- gRPC API: `localhost:6334`

## Monitoring

The service includes a configured healthcheck that:

- Checks health every 30 seconds
- Has a 10-second timeout
- Makes 3 retry attempts on failure
- Waits 40 seconds during initialization

## Data Persistence

Data is stored in the project's `data/` directory, which is mapped to `/qdrant/storage` inside the container.

## Network

The service runs on a dedicated Docker network called `qdrant-network` and is also connected to a `shared-network` for communication with other containers, providing isolation and security.

## Troubleshooting

If you encounter issues:

1. Check the logs:

```bash
docker compose logs qdrant
```

2. Check container status:

```bash
docker compose ps
```

3. Restart the service:

```bash
docker compose restart qdrant
```

## Contributing

Feel free to contribute improvements through pull requests.

## License

This project is under the same license as Qdrant.
