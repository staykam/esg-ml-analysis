# ESG Data Analysis via Machine Learning & Deep Learning
**BSc Capstone -- EU Business School - Corentin Lepla**

**Goal:** identify which ESG variables predict a firm's risk-adjusted efficiency (Sharpe ratio), independent of industry or geography.

**Premise / hypothesis:** ESG research fixates on ROI/ROA/ROE and rarely applies AI to noisy, nonlinear financial data; k-means + random forests should surface firm archetypes and score drivers that conventional rating aggregation misses.

**Status:** complete -- BSc Capstone thesis (graded). Full pipeline (ingest -> clean -> cluster -> model) in `notebooks/`.

## Research question
Does a firm's ESG profile explain its **risk-adjusted efficiency** (Sharpe ratio), rather than
the usual return metrics (ROI/ROA/ROE) -- and can machine learning identify which ESG variables
predict it, independent of industry or geography? The approach: k-means to find firm archetypes
from ESG scores (chosen by silhouette score and the elbow method), then a Random Forest Regressor
per cluster to predict the Sharpe ratio (evaluated by R^2 and MSE).

## Pipeline
| Stage | Notebook | What it does |
|-------|----------|--------------|
| 1. Ingest | `notebooks/01_reading_data.ipynb` | Load raw ESG data and assemble the working dataset |
| 2. Clean | `notebooks/02_removing_nans.ipynb` | Handle missing values and prepare a modelling-ready frame |
| 3. Model & cluster | `notebooks/03_analysis.ipynb` | k-means clustering of ESG profiles + random-forest prediction of the Sharpe ratio per cluster |

## Selected results
- **7 clusters** are optimal (silhouette score, corroborated by the elbow method); PCA shows the separation (`figures/snsplot.png`, `figures/kmeans.gif`).
- Random forests reach **R^2 ~= 0.99** (train and test), test **MSE ~= 2.35** (`figures/rf.png`).
- **Environmental and social** variables predict the Sharpe ratio; **governance** variables are not significant predictors in any cluster.
- Two variables predict efficiency **universally, regardless of industry or region**: *Sustainable Building Products* and *Resource Use* (H1 confirmed).
- Clusters mix all three ESG pillars rather than splitting into pure E/S/G leaders (H2 rejected) -- firms are better grouped by firm-specific ESG profile than by sector or geography.
- Firms combining **environmental innovation with strong, inclusive management practices** are the most risk-efficient.

## Data availability
The raw ESG dataset is from a licensed data provider and is **not redistributed** here.
The notebooks document the expected columns and format for reproduction.

## Write-up
The full BSc Capstone thesis is available on request.
