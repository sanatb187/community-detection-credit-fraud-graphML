# Community Detection for Credit Fraud

## Overview

This project explores whether graph-based analytics can help identify groups of customers who may be at higher risk of payment default or fraud. The idea is to move beyond isolated transaction analysis and instead study how customers relate to one another as part of a broader network.

The project uses the IEEE-CIS Credit Card Fraud Dataset and combines structured transaction features, graph community detection, and embeddings to study suspicious customer clusters. The goal is to compare traditional graph clustering methods with learned graph and text-based representations to see which approach gives more useful signals. :contentReference[oaicite:0]{index=0}

## Project Goal

The main objective is to build a workflow that:

- creates representative customer cohorts from transaction behavior
- enriches those cohorts with business or structural context
- converts the data into a graph format for Neo4j
- detects suspicious customer communities using graph algorithms
- generates combined graph and text embeddings
- compares both approaches for identifying potentially risky customer groups

## Planned Workflow

### 1. Project setup

Set up the project environment using `uv` for dependency and environment management. This keeps the project lightweight and reproducible. :contentReference[oaicite:1]{index=1}

### 2. Cohort creation with Polars

Use `polars` to build representative customer cohorts based on behavioral features such as:

- average transaction amount
- transaction frequency
- similar customer activity patterns

These cohorts serve as the foundation for later profiling and graph construction. :contentReference[oaicite:2]{index=2}

### 3. Initial profiling

Perform exploratory profiling on each representative cohort using `ydata-profiling`. This helps understand data quality, feature distributions, and differences across customer groups before graph construction begins. :contentReference[oaicite:3]{index=3}

### 4. Add business context

Add textual business or structural context to each cohort. This context is intended to capture information that may not be obvious from numeric features alone and can later be used for embedding generation. :contentReference[oaicite:4]{index=4}

### 5. Build the graph in Neo4j

Extract nodes and entities from the prepared data and ingest them into Neo4j. The graph should represent customers and relevant relationships between them. Batched ingestion will also be explored for efficiency. :contentReference[oaicite:5]{index=5}

### 6. Detect suspicious communities

Run initial graph analytics to identify potentially fraudulent or risky customer cliques using community detection methods such as:

- Louvain
- Leiden

This stage provides a first graph-based benchmark for suspicious cluster discovery. :contentReference[oaicite:6]{index=6}

### 7. Generate embeddings

Create richer representations of customers and cohorts by combining:

- graph embeddings using GraphSAGE
- text embeddings using sentence-transformers
- a custom embedding formed from a linear combination of both

This step is meant to capture both relational structure and business context in a unified representation. :contentReference[oaicite:7]{index=7}

### 8. Compare both approaches

Compare the results from:

- graph community detection methods
- hybrid graph and text embedding methods

The comparison will help evaluate which approach is more useful for identifying meaningful risky clusters in this dataset. :contentReference[oaicite:8]{index=8}

## Tech Stack

Planned tools and libraries include:

- Python
- uv
- Polars
- ydata-profiling
- Neo4j
- Louvain and Leiden community detection
- GraphSAGE
- sentence-transformers
- Graph Data Analytics and GraphML

## Expected Outcome

By the end of the project, the goal is to have a working pipeline that can:

- transform tabular fraud data into a graph representation
- identify suspicious communities of customers
- enrich graph analysis with business-aware text context
- compare classical graph algorithms with learned embedding approaches
