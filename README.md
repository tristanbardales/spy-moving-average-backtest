# SPY Moving Average Crossover Backtest

Does a simple trend-following strategy beat buy-and-hold? This project backtests a 50/200-day moving-average crossover strategy on 20 years of S&P 500 (SPY) data and compares its returns and risk to simply holding the index.

## Strategy

- **Invested** when the 50-day moving average is above the 200-day moving average
- **In cash** when the 50-day moving average falls below the 200-day moving average
- Trades execute the day after a signal to avoid look-ahead bias
- A 0.1% transaction cost is applied to every trade
-  Earns the 13-week Treasury bill rate while in cash

## Results (2005–2026)

| Metric | Buy & Hold | MA Crossover |
|---|---|---|
| Annualized Return | 11.29% | 9.56% |
| Volatility | 19.11% | 13.80% |
| Sharpe Ratio | 0.57 | 0.61 |
| Max Drawdown | -55.19% | -33.72% |

*Sharpe ratios are calculated using returns in excess of the 13-week T-bill rate.*

The strategy was invested 79% of the time and made 21 trades.

## Sub-Period Analysis

| Metric | B&H 2005–2015 | MA 2005–2015 | B&H 2016–2026 | MA 2016–2026 |
|---|---|---|---|---|
| Annualized Return | 7.65% | 9.14% | 14.86% | 9.95% |
| Volatility | 20.51% | 12.47% | 17.69% | 14.96% |
| Sharpe Ratio | 0.41 | 0.67 | 0.74 | 0.56 |
| Max Drawdown | -55.19% | -17.31% | -33.72% | -33.72% |

## Key Findings

Over the full period, the strategy gave up about 2% of annual return in exchange for lower volatility, a smaller maximum drawdown, and a slightly higher Sharpe ratio.

However, splitting the data shows that nearly all of this advantage came from avoiding the 2008 financial crisis, a slow-moving decline that gave the strategy time to exit. During the fast 2020 COVID crash, the strategy sold too late, took the full drawdown, and then missed much of the rebound while sitting in cash. In 2016–2026, it underperformed buy-and-hold on both return and risk-adjusted return.

**Takeaway:** The strategy's edge depends heavily on the type of market crash, and a strong full-period backtest can be driven by a single event. Testing across different time periods is essential before trusting any strategy.

## Limitations and Next Steps

- Prices are adjusted for dividends but taxes are not modeled
- Possible extensions: test other moving-average windows, other assets (international stocks, bonds), or volatility-based exit rules

## Tools

Python, pandas, NumPy, Matplotlib, yfinance (built in Google Colab)
