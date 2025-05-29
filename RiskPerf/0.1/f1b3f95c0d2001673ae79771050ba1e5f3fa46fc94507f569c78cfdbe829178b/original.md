```
capm(asset_returns, benchmark_returns; risk_free=0.0)
```

Calculates the CAPM α and β coefficients based on sample covariance statistics and a simple linear regression model.

The linear regression model looks as follows:

$r_a - r_f = α + β(r_b - r_f) + ϵ$

The α coefficient in this model is also known as Jensen's alpha. β is the slope coefficient, and ϵ is an error term.

# Arguments

  * `asset_returns`:      Vector of asset returns.
  * `benchmark_returns`:  Vector of benchmark returns (e.g. market portfolio returns for CAPM beta).
  * `risk_free`:          Optional vector or scalar value denoting the risk-free return (must have same frequency as the provided returns, e.g. daily).

# Returns

Tuple (α, β) with the estimated α and β coefficients of the CAPM model.
