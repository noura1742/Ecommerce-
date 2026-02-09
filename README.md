# End-to-End Analytics Data Pipeline (Postgres → dbt → ClickHouse)

## 📌 Overview
This project demonstrates an end-to-end analytics data pipeline following
modern data engineering best practices using a **Medallion Architecture**.

The pipeline ingests raw CSV data, transforms it using **dbt**, and prepares
analytics-ready data models for analytical querying.

---

## 🏗 Architecture

Bronze → Silver → Gold

- **Bronze**: Raw CSV data loaded into PostgreSQL
- **Silver**: dbt staging models (cleaning, renaming, type casting)
- **Gold**: Analytics models (Facts & Dimensions)
- **Target Warehouse**: ClickHouse

---

## 🛠 Tech Stack

- PostgreSQL (raw + staging)
- dbt (transformations & modeling)
- ClickHouse (analytics warehouse)
- Docker & Docker Compose

---

## 📊 Data Modeling

The project follows a **Galaxy Schema** design:

### Fact Tables
- `fact_orders`
- `fact_payments`
- `fact_feedback`

### Dimension Tables
- `dim_users`
- `dim_products`
- `dim_sellers`
- `dim_date`
- `dim_time`

Surrogate keys are generated for all fact tables.

---

## 🔁 dbt Layers

- **Sources**: Raw tables from PostgreSQL
- **Staging**: One model per source table
- **Intermediate**: Clean joins and grain control


---

## ▶️ How to Run

```bash
docker compose up -d
dbt run
dbt test
