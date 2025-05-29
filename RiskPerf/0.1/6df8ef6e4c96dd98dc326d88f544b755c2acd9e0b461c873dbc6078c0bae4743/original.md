```
sharpe_ratio(returns; multiplier=1.0, risk_free=0.0)
```

Calculates the Sharpe Ratio (SR) according to the original definition by William F. Sharpe in 1966. For calculating the Sharpe Ratio according to Sharpe's revision in 1994, please see function `information_ratio` (IR).

# Formula

$\text{SR} = \dfrac{\mathbb{E}\left[\text{returns} - \text{risk\_free} \right]}{\sigma(\text{returns})} \times \sqrt{\text{multiplier}}$

$\text{IR} = \dfrac{\mathbb{E}\left[\text{asset\_returns} - \text{benchmark\_returns} \right]}{\sigma(\text{asset\_returns} - \text{benchmark\_returns})} \times \sqrt{\text{multiplier}}$

# Arguments

  * `returns`:        Vector of asset returns.
  * `multiplier`:     Optional scalar multiplier, i.e. use `12` to annualize monthly returns, and use `252` to annualize daily returns.
  * `risk_free`:      Optional vector or scalar value denoting the risk-free return (must have same frequency as the provided returns, e.g. daily).

# Sources

  * Sharpe, W. F. (1966). Mutual Fund Performance. Journal of Business.
  * Sharpe, William F. (1994). The Sharpe Ratio. The Journal of Portfolio Management.
