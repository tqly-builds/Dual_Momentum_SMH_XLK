# Dual Momentum with SMH and XLU

Code for the paper **"Dual Momentum in Equity-Utility Portfolios: Empirical Performance, Risk-Adjusted Returns, and Volatility Dynamics"** by Thanh Ly (MSBA Program, California State University, Sacramento). ORCID: [0009-0002-5249-7955](https://orcid.org/0009-0002-5249-7955)

The notebook backtests a dual-momentum rule over four ETFs:

| Ticker | Role |
|---|---|
| SMH | Asset A (semiconductors, growth) |
| XLU | Asset B (utilities, defensive) |
| GLD | Safe haven |
| BIL | Cash proxy / risk-free hurdle |

Each month-end, the rule picks whichever of SMH and XLU had the higher 12-month return (relative momentum). It holds that asset only if its 12-month return beat BIL; otherwise it holds GLD (absolute momentum). The signal is applied to the next month's return, and each position change costs 10 bps.

The notebook compares the rule against SMH buy-and-hold, a 50/50 SMH-XLU mix, and relative momentum only. It also runs transaction-cost and look-back sensitivity tests and fits a GARCH(1,1) model to the strategy's returns.

**Data:** monthly adjusted closes from Yahoo Finance via `yfinance`, May 2007 to July 2026. The evaluation period is June 2008 to July 2026 (218 months).

## How to run

```bash
pip install -r requirements.txt
jupyter notebook dual_momentum_smh_xlu.ipynb
```

Run all cells from top to bottom.

- On the first run, the notebook downloads prices and saves them to `data/monthly_prices.csv`. Later runs reuse that file, so results stay the same even if Yahoo later revises adjusted prices. Delete the file to download fresh data.
- Figures 1–3 of the paper are saved to `figures/` at 300 dpi.
- Every table in the paper is saved as a CSV in `results/`.

## Repository contents

```
dual_momentum_smh_xlu.ipynb   main notebook (all results, tables and figures)
requirements.txt              Python dependencies
data/monthly_prices.csv       month-end prices used in the paper (created on first run)
figures/                      Figures 1-3 (created on run)
results/                      result tables as CSV (created on run)
```

## Citation

Ly, T. (2026). *SMH vs XLU dual-momentum backtest* [Jupyter notebook]. GitHub. https://github.com/tqly-builds/dual_momentum_smh_xlk

## License

MIT. See `LICENSE`.
