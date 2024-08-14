# Coin API Monitoring Stack

This repository contains the Docker Compose setup for a comprehensive monitoring stack for the Coin API. It includes Prometheus for metrics collection, Grafana for data visualization, Alertmanager for managing alerts, cAdvisor for monitoring container performance, and a custom alert integration with Discord.

## Services Included

- **coin-api**: The main API providing data, built from a local Dockerfile.
- **cadvisor**: Monitors container metrics.
- **prometheus**: Scrapes and stores metrics from various services.
- **alertmanager**: Manages alerts, configured to send notifications via Discord.
- **discord-alerts**: Forwards alerts to a specified Discord channel.
- **grafana**: Visualizes metrics through dashboards.

## Prerequisites

- Docker and Docker Compose installed on your system.
- Basic knowledge of Docker containerization and Docker Compose.

## Setup Instructions

1. **Set up environment variables**:
   - Copy the `.env.sample` file to `.env` and fill in the necessary environment variables such as `DISCORD_WEBHOOK_URL`.

2. **Start the services**:
   - Run the following command to start all services:
     ```bash
     docker-compose up -d --build
     ```

3. **Access the services**:
   - **Grafana**: Accessible at `http://localhost:3000`. Default login is `admin/admin`, which you should change immediately.
   - **Prometheus**: Accessible at `http://localhost:9090`.
   - **Alertmanager**: Accessible at `http://localhost:9093`.
   - **cAdvisor**: Accessible indirectly via Prometheus scraping its metrics.

## Configuration

- **Prometheus**: Configured via `./prometheus/prometheus.yml`.
- **Grafana**: Configured via the provisioning files located in `./grafana/provisioning`.
- **Alertmanager**: Configured via `./alertmanager/alertmanager.yml`.

## Stopping and Removing Services

- To stop all services:
  ```bash
  docker-compose down
  ```
- To remove all data and clean up:
  ```bash
  docker-compose down -v
  ```

## Troubleshooting

- If services fail to start, check the Docker logs for the specific service using:
  ```bash
  docker logs <service-name>
  ```

