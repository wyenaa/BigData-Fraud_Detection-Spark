# 🛡️ Scalable Fraud Detection System with Apache Spark & Hadoop

![Apache Spark](https://img.shields.io/badge/Apache%20Spark-PySpark-orange)
![Hadoop](https://img.shields.io/badge/Hadoop-HDFS%20%7C%20YARN-yellow)
![Status](https://img.shields.io/badge/Status-Completed-success)

## Project Overview
This project demonstrates a **Big Data pipeline** designed to detect fraudulent financial transactions. Unlike traditional pipelines using Pandas which are limited by single-machine memory, this system is built on top of the **Hadoop Ecosystem** using **Apache Spark** for distributed processing.

The goal is to handle large-scale datasets efficiently, performing ETL (Extract, Transform, Load) and Machine Learning classification in a distributed environment.

## Architecture & Tech Stack

This project was deployed on a **Multi-Node Hadoop Cluster** running on Ubuntu Linux.

| Component | Technology | Role in Project |
| :--- | :--- | :--- |
| **Storage** | **HDFS** (Hadoop Distributed File System) | Stores raw transaction data reliably across the cluster. |
| **Resource Manager** | **YARN** | Manages CPU/RAM allocation for Spark jobs. |
| **Processing** | **Apache Spark (PySpark)** | Performs in-memory distributed data processing and ML modeling. |
| **OS** | Ubuntu Linux | Underlying infrastructure managed via CLI. |

## Key Features Implemented

### 1. Infrastructure Setup (Data Engineering)
* Configured Hadoop core components (`core-site.xml`, `hdfs-site.xml`, `yarn-site.xml`, `hadoop-env.sh`) and Java environment variables.
* Managed HDFS commands (`hdfs dfs -put`, `ls`, `mkdir`) to ingest raw CSV data from local storage to the distributed file system.

### 2. Distributed Data Processing (ETL)
* Utilized **SparkSession** to ingest data into Spark DataFrames.
* Performed schema validation and type casting (e.g., converting `amount` to Double).
* Handled missing values and feature engineering using **VectorAssembler** and **StringIndexer** to prepare data for ML models.

### 3. Scalable Fraud Detection (Binary Classification)
* Modeling: Engineered a distributed fraud detection pipeline using PySpark MLlib's Random Forest Classifier to handle massive transaction datasets efficiently.
* Evaluation Strategy: Prioritized Recall to minimize missed fraud cases (False Negatives), ensuring high security reliability.

## Key Results
* **Model Performance:** Achieved exceptional predictive power with **96.40% Recall and 92.94% Precision.**
* **Reliability:** The model demonstrated high stability with an F1-Score of 94.64%, proving it effectively catches fraud without causing excessive false alarms for genuine customers.
* **Tech Stack:** HDFS, YARN, PySpark (MLlib).

## 🚀 How to Run
1.  Ensure Hadoop (HDFS & YARN) services are running:
    ```bash
    start-dfs.sh
    start-yarn.sh
    ```
2.  Submit the Spark job:
    ```bash
    spark-submit fraud_detection.py
    ```

---
**Created by Wyena Suilianty**
*Big Data & Analytics Portfolio*
