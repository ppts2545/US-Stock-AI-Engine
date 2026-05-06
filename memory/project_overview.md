---
name: Project Overview
description: US Stock Prediction Model project structure, goals, and known issues
type: project
---

Multi-notebook ML project predicting US stock price direction.

**Pipeline:**
1. `src/01get_stock_data.ipynb` — downloads OHLCV via yfinance for 7 tickers (AAPL, MSFT, NVDA, JPM, BAC, TSLA, AMZN) 2015–2025 → `data/raw/*.csv`
2. `notebook/feature/02_features.ipynb` — computes TA indicators (ta library), lags them by 1 day, target = 5-day forward return > 1% → `data/processed/features/features_all.csv`
3. `notebook/feature/Sentiment Signals.ipynb` — FinBERT sentiment on yfinance news for a single ticker (AAPL), needs NEWSAPI_KEY env var
4. `notebook/model/baseline.ipynb` — RandomForestClassifier on features_all.csv, train < 2022, test >= 2022

**Target definition:** 5-day forward return > 1% (binary). Features are lag-1 (yesterday's indicators).

**Why:** User wanted to fix all bugs in the project.

**How to apply:** Keep target consistent as 5-day >1% across all notebooks. Features are engineered indicators only (exclude raw OHLCV from model inputs).
