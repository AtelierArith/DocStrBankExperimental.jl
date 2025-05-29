```
backtest(px, obs, hold, lower, upper; rf = 0.0, fullinvest=true,
```

denoise=true, method = "MSR")

Backtest optimal portfolio allocations. At any t, historical price data from t-obs-2 to t-1 (a total of obs number of return points) are used to compute optimal portfolio. This portfolio is held till t + hold and then the process is repeated. Transaction costs are assumed to be zero.

Return net asset value, allocations and index of rebalance times.
