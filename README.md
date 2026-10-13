# Quantitative-Portfolio-analyzer

A Python-based financial analysis environment designed to automate investment decision-making, audit risk exposure, and evaluate compliance with the guidelines of an Investment Policy Statement (IPS).

## 🎯 The Problem it Solves
Most retail investors make decisions based on intuition, market narratives, and superficial analysis, resulting in poor risk management (excess Beta, sector overexposure, or lack of true diversification). 

This project solves that problem by bringing institutional management practices (Hedge Funds) to a personal portfolio. The system does not tell you "what to buy" based on opinions, but rather mathematically audits your capital to answer critical questions:
- *Will my portfolio survive a -2σ risk event (Black Swan)?*
- *Am I truly diversified, or are my assets 80% correlated?*
- *Do my returns stem from my skill (Alpha), or simply from taking on excess risk in Growth stocks?*

## ⚙️ System Architecture (Modules)

The code is structured around 4 analytical engines:

### 1. Fundamental Analysis (Stock Screener)
Extracts real-time data from Yahoo Finance to audit the financial health and valuation of any company. It evaluates key Value Investing metrics such as P/E, PEG, EV/EBITDA, ROE, and leverage levels (Debt to Equity).

### 2. Stress Engine and Monte Carlo Simulation
Performs *Historical Bootstrapping* (sampling real returns with replacement) to generate 10,000 possible futures for the portfolio and its benchmark (S&P 500). 
- Calculates VaR (Value at Risk) and CVaR at 95%.
- Measures *Tracking Error* in extreme scenarios. If the projected loss exceeds the risk limit tolerated in the IPS, the system triggers a restructuring alert.

### 3. Machine Learning (Short-Term Tactical Projection)
Uses a `RandomForestRegressor` trained on hundreds of thousands of historical data points (prices, volume, volatility, technical oscillators) from S&P 500 companies to identify price inefficiencies and project expected growth over 2 months.

### 4. Institutional Analysis (Quantitative Audit)
- **Covariance Matrix:** Measures the true Diversification Benefit and the isolated vs. interactive risk of the portfolio.
- **GARCH (1,1) Model:** Projects conditional volatility over 5 days for tactical liquidity management (*dry powder*).
- **Fama-French 3-Factor Model:** Executes an OLS regression against the Kenneth French data library to decompose returns into exposure to the Market (MKT), Size (SMB), and Value (HML).

## 🛠️ Tech Stack
- **Language:** Python
- **Financial/Econometric Libraries:** `yfinance`, `arch` (GARCH), `statsmodels` (OLS/Fama-French), `pandas_datareader`.
- **Machine Learning:** `scikit-learn` (Random Forest).
- **Computation & Visualization:** `numpy`, `pandas`, `scipy.stats`, `matplotlib`, `seaborn`.

## ✍️ About the Author and Development
**Samuel Francisco Chavarro Hernández**  
*Economics and International Finance / Engineering Student*

This project stems from the intersection of the rigor of engineering systems thinking and advanced portfolio theory. 
*Technology transparency note:* All financial architecture, the design of the Investment Policy Statement (IPS), the selection of statistical models (Bootstrapping, GARCH, Fama-French), and the risk management parameters were conceptually developed entirely on my own. The writing and execution of the Python syntax were accelerated and optimized using Artificial Intelligence tools as development assistants.
