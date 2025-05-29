```
modified_jensen(asset_returns, benchmark_returns; risk_free=0.0)
```

Divides Jensen’s alpha by the systematic risk, which measures the systematic risk-adjusted return per unit of systematic risk. See also `jensen_alpha`

# Arguments

  * `asset_returns`:      Vector of asset returns.
  * `benchmark_returns`:  Vector of benchmark returns (e.g. market portfolio returns for CAPM beta).
  * `risk_free`:          Optional vector or scalar value denoting the risk-free return (must have same frequency as the provided returns, e.g. daily).

# Returns

Modified Jensen's alpha measure.

# Sources

  * Bacon, Carl (2008). Practical Portfolio Performance Measurement and Attribution, 2nd Edition, John Wiley & Sons Ltd. Page 77.
