# Periodicity Analysis

A Python-based analytical toolkit for detecting and classifying recurring patterns in financial transaction data. This project identifies periodic transactions (weekly, monthly, quarterly) by analyzing transaction dates, amounts, and narrations.

## Overview

Financial transactions often follow predictable patterns—recurring payments, subscriptions, salary deposits, or regular expenses. This repository provides tools to automatically detect and classify these periodic patterns from banking and credit transaction data.

## Features

- **Date Periodicity Detection**: Identifies transactions that occur at regular time intervals (weekly, monthly, quarterly)
- **Amount Periodicity Analysis**: Detects transactions with consistent or near-consistent amounts
- **Confidence Scoring**: Assigns reliability scores based on pattern consistency and frequency
- **Multi-dimensional Analysis**: Combines date gaps and amount variations for robust detection
- **Excel Integration**: Reads and processes transaction data from Excel files, outputs results to Excel

## Project Structure

```
├── date_periodicity.ipynb          # Weekly, monthly, and quarterly pattern detection
├── amount_date_periodicity.ipynb   # Combined date and amount analysis with confidence scoring
└── README.md                        # This file
```

## Notebooks

### `date_periodicity.ipynb`
Analyzes temporal patterns in transactions by examining:
- **Monthly Patterns**: Transactions with consistent day-of-month (e.g., always on the 5th)
- **Weekly Patterns**: Transactions on the same day of the week
- **Quarterly Patterns**: Transactions occurring at quarterly intervals

### `amount_date_periodicity.ipynb`
Performs comprehensive periodicity analysis including:
- **Date Periodicity Score**: Based on gaps between transaction dates (25-35 days for monthly, 85-95 days for quarterly)
- **Amount Periodicity Score**: Based on consistency of transaction amounts (±5% tolerance)
- **Confidence Score**: Combined score (0-160 range) indicating the reliability of the periodicity classification

## Installation

### Requirements
- Python 3.7+
- pandas
- numpy
- openpyxl (for Excel file handling)

### Setup

```bash
# Install required packages
pip install pandas numpy openpyxl
```

## Usage

1. **Prepare Data**: Ensure your transaction data is in Excel format with columns for:
   - `Date`: Transaction date
   - `Amount`: Transaction amount
   - `Narration` or `Cleaned Narration`: Transaction description

2. **Run Analysis**:
   - Open `date_periodicity.ipynb` for temporal pattern detection
   - Open `amount_date_periodicity.ipynb` for combined analysis with scoring

3. **Review Results**: Output files will contain:
   - Periodicity classification (Weekly/Monthly/Quarterly)
   - Confidence scores for each transaction
   - Pattern statistics (date gaps, amount consistency)

## Key Functions

**Date Periodicity Score**: Evaluates how consistently transactions occur at expected intervals
- 80 points: Monthly (gaps 25-35 days with >60% consistency) or Quarterly (gaps 85-95 days)
- 50 points: Lower consistency patterns
- 0 points: No periodic pattern detected

**Amount Periodicity Score**: Evaluates amount consistency across transactions
- 80 points: >70% of amounts within ±5%
- 40 points: 40-70% of amounts within ±5%
- 0 points: No amount pattern detected

**Confidence Score**: Sum of both scores (0-160 range)

## Data Requirements

Input data should include:
- Transaction date in a parseable format (e.g., YYYY-MM-DD)
- Transaction amount as numeric values
- Transaction narration/description for grouping

## Use Cases

- **Personal Finance**: Identify recurring bills and subscriptions
- **Banking Analytics**: Detect patterns for transaction categorization
- **Fraud Detection**: Identify anomalies in expected periodic transactions
- **Financial Planning**: Categorize regular vs. irregular expenses