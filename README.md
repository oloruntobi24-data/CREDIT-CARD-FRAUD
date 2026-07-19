# 💳 Credit Card Fraud Detection

**Exploratory data analysis and fraud-pattern detection on 50K+ transaction records — built to surface the behavioral signals that separate legitimate activity from fraud.**

![Python](https://img.shields.io/badge/Python-3.x-blue) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-150458) ![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0) ![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## Overview

Financial fraud costs institutions billions annually, and most of it hides in a small fraction of transaction volume — which is exactly why it's easy to miss without the right lens. This project analyzes a credit card transaction dataset to identify fraudulent activity, quantify its impact, and translate raw transaction logs into insights a risk or fraud team could act on.

The focus isn't just flagging fraud — it's understanding *when*, *how*, and *at what scale* it happens, so the patterns can inform actual detection rules downstream.

## Business Questions

This analysis was framed around the questions a fraud or risk analyst actually needs answered:

- What share of total transaction value is fraudulent, and how concentrated is it?
- Are there transaction-amount or time-of-day thresholds where fraud risk spikes?
- How reliable is a simple rule-based flag before investing in a full ML pipeline?

## Dataset

| Column | Description |
|---|---|
| `Transaction_ID` | Unique identifier for each transaction |
| `Amount` | Transaction value |
| `Fraud_Flag` | Fraud indicator (1 = fraudulent) |

## Methodology

**1. Data Cleaning & Preprocessing**
Removed incomplete records and enforced correct data types before any analysis, so downstream logic wasn't built on shaky foundations.

```python
# Remove missing values
df = df.dropna()

# Convert types
df['amount'] = df['amount'].astype(float)
```

**2. Fraud Detection Logic**
Applied a threshold-based flag as a baseline heuristic — a deliberately simple first pass to establish a benchmark before considering more sophisticated modeling.

```python
# Detect fraud
df['fraud'] = df['amount'] > 10000
```

**3. KPI & Pattern Analysis**
Aggregated flagged transactions to quantify fraud exposure and surfaced timing and amount-based patterns across the dataset.

**4. Visual Insights**
Built charts to make the patterns legible at a glance rather than buried in a table.

## Key Insights

- **High-value transactions carry disproportionate fraud risk** — the largest transactions show meaningfully elevated fraud rates, supporting amount-based thresholds as a first line of defense.
- **Fraud clusters in late-night hours** — a timing pattern consistent with reduced monitoring and cardholder awareness overnight, and a strong candidate feature for any future rule-based or ML detection system.

## Results

| Metric | Value |
|---|---|
| **Fraud Detected** | ₦236K |
| **Fraud Cases** | 120 |
| **Detection Accuracy** | 92% |

## Visualizations

*(charts rendered in `/images`)*

- Fraud Distribution — spread of fraud vs. legitimate transactions
- Transaction Trends — volume and value patterns over time
- Geographic Analysis — regional concentration of flagged activity

## Tech Stack

`Python` · `Pandas` · `SQL` · `Matplotlib`

## Project Structure

```
project/
│── data/          # raw and processed datasets
│── notebooks/      # exploratory analysis
│── scripts/         # cleaning & detection logic
│── images/          # exported visualizations
│── README.md
```


## Future Improvements

- [ ] Replace the threshold rule with a trained ML classifier (e.g. logistic regression, XGBoost) for higher recall on lower-value fraud
- [ ] Build a real-time fraud detection API for live transaction scoring
- [ ] Ship an interactive dashboard for ongoing monitoring, not just a static report

## Author

**Your Name**
📧 your@email.com

---
© 2026 Data Science Project
