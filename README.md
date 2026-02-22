# Time-Series-Structural-Break-Detection

A proposed method for detecting structural breaks in financial time series using the **two-sample Kolmogorov-Smirnov (KS) test**. Developed as part of a thesis research project.

---

## Overview

Structural breaks — sudden shifts in the statistical properties of a time series — can significantly impact forecasting models and trading strategies. This project proposes a non-parametric approach to detecting such breaks by applying the **two-sample Kolmogorov-Smirnov test** to rolling windows of financial return data.

The method is applied to real-world stock price data for three major companies:

- **Amazon (AMZN)**
- **Google (GOOGL)**
- **Netflix (NFLX)**

---

## Method

The two-sample KS test compares the empirical cumulative distribution functions (ECDFs) of two data samples to determine whether they come from the same underlying distribution. In the context of structural break detection:

1. A rolling window is applied to the time series.
2. For each position, the KS test compares the distribution of returns in two adjacent windows.
3. A statistically significant difference (low p-value) is flagged as a potential structural break.

This is a **non-parametric** method, meaning it makes no assumptions about the underlying distribution of returns — making it robust to fat tails and non-normality common in financial data.

---

## Repository Structure
```
Time-Series-Structural-Break-Detection/
│
├── AMZN.xlsx                  # Amazon historical stock price data
├── GOOGL.xlsx                 # Google historical stock price data
├── NFLX.xlsx                  # Netflix historical stock price data
│
├── Time_Series_AMZN.ipynb     # KS-based structural break analysis for Amazon
├── Time_Series_GOOGL.ipynb    # KS-based structural break analysis for Google
├── Time_Series_NFLX.ipynb     # KS-based structural break analysis for Netflix
│
├── LICENSE                    # Apache-2.0 License
└── README.md
```

---

## Requirements

This project is built in Python using Jupyter Notebooks. The following libraries are required:
```
pandas
numpy
scipy
matplotlib
openpyxl
```

Install dependencies via pip:
```bash
pip install pandas numpy scipy matplotlib openpyxl
```

---

## Getting Started

1. **Clone the repository:**
```bash
git clone https://github.com/steveparakal/Time-Series-Structural-Break-Detection.git
cd Time-Series-Structural-Break-Detection
```

2. **Install dependencies** (see above).

3. **Launch Jupyter Notebook:**
```bash
jupyter notebook
```

4. **Open any of the three notebooks** (`Time_Series_AMZN.ipynb`, `Time_Series_GOOGL.ipynb`, or `Time_Series_NFLX.ipynb`) and run the cells to reproduce the analysis.

---

## Data

The `.xlsx` files contain historical stock price data for AMZN, GOOGL, and NFLX. The notebooks load these files directly and compute log returns or price differences before applying the KS test.

---

## Results

Each notebook outputs:

- A time series plot of the stock's closing prices or returns.
- KS test statistics and p-values computed over rolling windows.
- Identified breakpoints where the null hypothesis of distributional equality is rejected.

---

## License

This project is licensed under the [Apache-2.0 License](LICENSE).

---

## Citation

If you use this work in your own research, please cite accordingly:
```
steveparakal. (2024). Time-Series-Structural-Break-Detection.
GitHub. https://github.com/steveparakal/Time-Series-Structural-Break-Detection
```

---

## Acknowledgements

This project was developed as part of a thesis on structural break detection in financial time series. The Kolmogorov-Smirnov test is implemented using [`scipy.stats.ks_2samp`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.ks_2samp.html).
