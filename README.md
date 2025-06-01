# 🚀 Automated ETL Pipeline for NASA API Using Apache Airflow, PostgreSQL & Docker

## 📌 Project Overview

This project demonstrates a fully automated, containerized ETL (Extract, Transform, Load) data pipeline built with **Apache Airflow**, integrated with **NASA’s Astronomy Picture of the Day (APOD) API**, and backed by a **PostgreSQL** database. The pipeline is designed for scalability, reliability, and automation, and runs within an isolated Dockerized environment.

## 🎯 Key Objectives

- **Automate** daily data extraction from the NASA APOD API.
- **Transform** raw JSON data into structured, analysis-ready format.
- **Load** curated data into a PostgreSQL database for long-term storage and potential downstream use (e.g., analytics, dashboards).

## 🧱 Core Components

### 🛠 Apache Airflow – Orchestration

- Defines and schedules the ETL pipeline via a Directed Acyclic Graph (DAG).
- Manages task dependencies to ensure robust execution.
- Uses `SimpleHttpOperator`, `PythonOperator`, and `PostgresOperator` for modular task design.

### 🛰 NASA APOD API – Data Source

- Provides daily astronomy image metadata (title, explanation, media URL, and date).
- Data is fetched via Airflow’s `SimpleHttpOperator`.

### 🗃 PostgreSQL – Data Storage

- Stores transformed API data in a persistent, structured schema.
- Runs in a Docker container with volumes for data durability.
- Managed via Airflow’s `PostgresHook` and SQL-based schema initialization.

### 🐳 Docker – Containerization

- Runs Airflow and PostgreSQL as isolated services.
- Ensures reproducibility, scalability, and easy deployment.

## 🔄 ETL Workflow Overview

1. **Extract**
   - Scheduled daily data fetch from the NASA APOD API.
   - API response captured in JSON format.

2. **Transform**
   - Filters and formats fields like `title`, `explanation`, `url`, and `date`.
   - Implemented using Airflow's TaskFlow API (`@task` decorator).

3. **Load**
   - Inserts cleaned data into PostgreSQL.
   - Creates target table if it doesn't already exist.

## 📂 Folder Structure

```
├── dags/
│   └── nasa_apod_etl.py         # Main Airflow DAG
├── docker-compose.yml           # Docker orchestration
├── requirements.txt             # Python dependencies
├── .env                         # Environment variables (e.g., API key)
└── README.md                    # Project documentation
```

## ✅ Why This Project Stands Out

- Combines API integration, orchestration, transformation logic, and database persistence in a real-world scenario.
- Demonstrates fluency in modern data engineering tools: Airflow, Docker, PostgreSQL.
- Easily extensible to other APIs and workflows.

## 🚀 Future Enhancements

- Add data quality checks and error handling with Airflow sensors.
- Integrate visualization tools like Metabase or Superset.
- Extend to multiple APIs or time ranges for batch ingestion.
