```
sortino_ratio(returns; multiplier=1.0, risk_free=0.0)
```

Calculates the Sortino Ratio, a downside risk-adjusted performance measure. Contrary to the Sharpe Ratio, only deviations below the minimum acceptable returns are included in the calculation of the risk (downside deviation instead of standard deviation).

# Arguments

  * `returns`:        Vector of asset returns.
  * `multiplier`:     Optional scalar multiplier, i.e. use `12` to annualize monthly returns, and use `252` to annualize daily returns.
  * `MAR`:            Optional vector or scalar value denoting the minimum acceptable return(s). Must have same frequency as the provided returns, e.g. daily.

# Formula

$\text{Sortino Ratio} = \dfrac{\text{returns} - \text{MAR}}{\text{downside deviation}} \times \sqrt{\text{multiplier}}$

The downside deviation is simply the standard deviation of the returns below the minimum acceptable return.

# Sources

  * Sortino, F. and Price, L. (1996). Performance Measurement in a Downside Risk Framework. Journal of Investing.
