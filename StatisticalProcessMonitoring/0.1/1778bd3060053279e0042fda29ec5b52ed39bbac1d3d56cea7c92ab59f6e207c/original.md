```
DiagMEWMA(Λ, value)
```

Exponentially weighted moving average with diagonal smoothing matrix `Λ` and initial value `value`.

The update mechanism based on a new observation `x` is given by

$Z_t = (I-Λ)Z_{t-1} + Λ x_t$,

and the chart value is defined as

$C_t = Z_t' Λ^{-1} Z_t$.

### Arguments

  * `Λ::Vector{Float64}`: The vector of smoothing constants.
  * `value::Float64`: Current value of the statistic (default = 0.0).
  * `z::Vector{Float64}`: Vector of smoothed observations (Default: `zeros(length(Λ))`).
  * `inv_Σz::Matrix{Float64}`: Inverse of the covariance matrix of the control variates.

### References

Lowry, C. A., Woodall, W. H., Champ, C. W., & Rigdon, S. E. (1992). A Multivariate Exponentially Weighted Moving Average Control Chart. Technometrics, 34(1), 46-53. https://doi.org/10.1080/00401706.1992.10485232
