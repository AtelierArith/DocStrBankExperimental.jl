```
tracking_error(asset_returns, benchmark_returns; multiplier=1.0)
```

Calculates the ex-post Tracking Error based on the standard deviation of the active returns.

# Formula

$\text{TE} = \sigma\left( \text{asset\_returns} - \text{benchmark\_returns} \right) \times \sqrt{\text{multiplier}}$

# Arguments

  * `asset_returns`:      Vector of asset returns.
  * `benchmark_returns`:  Vector of benchmark returns.
  * `multiplier`:         Optional scalar multiplier, i.e. use `12` to annualize monthly returns, and use `252` to annualize daily returns.
