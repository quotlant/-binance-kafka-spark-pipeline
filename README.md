# Crypto Market Data Pipeline

## Overview

This project is an end-to-end real-time cryptocurrency data engineering pipeline built using modern data engineering tools. The pipeline ingests live cryptocurrency market data from the Binance API, stores raw data in PostgreSQL, streams data through Apache Kafka, processes it using Apache Spark Streaming, and stores aggregated analytics in Cassandra.

The project demonstrates batch and streaming architecture, workflow orchestration, distributed processing, and scalable data storage.

---

## Architecture Diagram

text Binance API │ ▼ Airflow DAG │ ▼ PostgreSQL (Raw) │ ▼ Kafka Topics │ ▼ Spark Streaming │ ▼ Cassandra (Processed) │ ▼ Analytics Layer

---

## Technologies Used

- Python
- Apache Airflow
- PostgreSQL
- Apache Kafka
- Apache Spark
- Cassandra
- Docker
- Binance API
- Pandas

---

## Project Structure

text crypto-market-data-pipeline/ │ ├── airflow/ │ └── dags/ │ ├── ingestion/ │ ├── kafka/ │ ├── spark/ │ ├── cassandra/ │ ├── sql/ │ ├── config/ │ ├── docs/ │ ├── tests/ │ ├── .env.example ├── .gitignore ├── docker-compose.yml ├── requirements.txt └── README.md

---

## Pipeline Workflow

### 1. Data Ingestion Layer

Airflow schedules data ingestion jobs that fetch cryptocurrency market data from the Binance API.

Data collected includes:

- Symbol
- Price
- Trade information
- Timestamp

---

### 2. Staging Layer

Raw cryptocurrency data is stored in PostgreSQL.

Example tables:

- prices
- trades
- symbols

---

### 3. Streaming Layer

Kafka streams data from PostgreSQL into Kafka topics for real-time processing.

Example topics:

- crypto_prices
- crypto_trades

---

### 4. Processing Layer

Apache Spark Streaming consumes Kafka topics and performs real-time transformations.

Metrics calculated include:

- Minute-level average prices
- Trade volume
- Price volatility
- Market trend analytics

---

### 5. Serving Layer

Processed metrics are written to Cassandra for fast querying and analytics.

---

## Environment Variables

Create a .env file based on .env.example.

Example:

env BINANCE_API_KEY= BINANCE_SECRET_KEY= POSTGRES_USER=admin POSTGRES_PASSWORD=password POSTGRES_DB=crypto_pipeline KAFKA_BOOTSTRAP_SERVERS=localhost:9092 CASSANDRA_HOST=localhost

---

## Installation

### Clone Repository

bash git clone https://github.com/yourusername/crypto-market-data-pipeline.git cd crypto-market-data-pipeline

### Install Dependencies

bash pip install -r requirements.txt

### Start Infrastructure

bash docker compose up -d

---

## Running The Pipeline

### Start Airflow

bash airflow standalone

### Start Spark Streaming

bash spark-submit spark/stream_processor.py

---

## Expected Outputs

The pipeline produces:

- Real-time cryptocurrency prices
- Minute-level average price metrics
- Trade volume metrics
- Volatility calculations
- Processed analytics stored in Cassandra

---

## Security

- Secrets are stored in .env
- .env is excluded using .gitignore
- No API keys are committed to GitHub

---

## Future Improvements

- Kraken API integration
- Real-time dashboards
- Schema Registry integration
- Anomaly detection
- Exchange comparison analytics
- API layer for querying Cassandra

---

## Author

Peter Amoro

Data Engineering Capstone Project
