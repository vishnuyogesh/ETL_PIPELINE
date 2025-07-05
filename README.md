# 🚀 Airflow ETL Pipeline with NASA API & PostgreSQL
This project shows how to build an ETL pipeline using Apache Airflow, PostgreSQL, and data from NASA's Astronomy Picture of the Day (APOD) API — all running in Docker containers.

The pipeline automatically fetches data daily from the NASA API, processes it, and stores it in a PostgreSQL database for future use (e.g., analysis, dashboards, or fun space facts! 🪐).

## 📌 What This Project Does
Extract data from the NASA APOD API (title, image URL, explanation, and date).

Transform the data into a clean format.

Load it into a PostgreSQL database.

All of this is automated using Apache Airflow and scheduled to run daily.

## 🧱 Key Tools Used
### Tool	        Purpose
Airflow      	Orchestrates the ETL process with a daily schedule
PostgreSQL	    Stores the final, processed data
NASA APOD API	Provides interesting astronomy data
Docker	        Runs Airflow & Postgres in isolated containers

## ⚙️ How the Pipeline Works 
  ###  A[Start DAG Daily] --> B[Extract from NASA API]
  ###  B --> C[Transform JSON Data]
  ###  C --> D[Create Table if Needed]
  ###  D --> E[Load into PostgreSQL]
#### 1. Extract
Airflow uses the SimpleHttpOperator to call NASA's APOD API.

#### 2. Transform
Using Airflow’s @task decorator (TaskFlow API), it filters and prepares the data.

### 3. Load
The PostgresHook inserts the data into a PostgreSQL table. If the table doesn’t exist, it is created automatically.

#### 🐳 Dockerized Setup
Everything runs in Docker containers, making setup super easy and reproducible.

### Services:
airflow-webserver

airflow-scheduler

airflow-worker

postgres

pgadmin (optional for viewing the database)

## ✅ How to Run This Project
#### Clone the Repo
git clone https://github.com/vishnuyogesh/ETL_PIPELINE.git
cd ETL_PIPELINE
Add Your NASA API Key

#### Create a .env file and add:
NASA_API_KEY=your_actual_api_key_here

#### Start the Project with Docker
docker-compose up --build
Open Airflow

Visit: http://localhost:8080
Login: admin / admin

#### Trigger the DAG

Find the DAG named nasa_apod_etl and trigger it manually or let it run daily.

## 🗃️ Output Example
The final Postgres table will have entries like:

date	title	explanation	url
2025-07-05	Black Hole and Friends	A fun explanation...	https://apod.nasa.gov/...

### 📚 Learning Goals
Learn how to build an ETL workflow

Use Airflow's DAGs, hooks, and operators

Work with real-world APIs

Store clean data in a database

Practice Docker-based data engineering setups

#🧑‍💻 Author
## Vishnu Yogesh
### I built this project to explore data pipelines, automation, and astronomy APIs.
### Feel free to ⭐ star the repo or connect with me for feedback or collaboration!

