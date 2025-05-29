```
drawdowns(returns; compound)
```

Calculates the drawdown based on a returns time series.

# Arguments

  * `returns`:    Vector of asset returns (usually log-returns).
  * `geometric`:  Use geometric compounding (`cumprod`) if set to `true`, otherwise simple arithmetic sum (`cumsum`), e.g. for log-returns (default).
