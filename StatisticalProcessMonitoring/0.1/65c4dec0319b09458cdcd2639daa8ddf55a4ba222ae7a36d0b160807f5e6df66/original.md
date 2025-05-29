```
NEWMA
```

A Nonparametric Exponentially Weighted Moving Average statistic for monitoring profiles.

# Fields

  * `λ::Float64`: The EWMA smoothing constant. Must be between 0 and 1.
  * `value::Float64`: The current value of the NEWMA statistic.
  * `σ::Float64`: The standard deviation of the error term.
  * `cdf_σ::E`: A function that computes the (estimated) cdf of the error term `σ` with signature `cdf_σ(x::Real)`.
  * `g::F`: The estimated regression function object. Must have a method of signature `predict(g::F, x::AbstractVector)`.
  * `Ej::Vector{Float64}`: The current smoothed observations.

# References

Zou, C., Tsung, F., & Wang, Z. (2008). Monitoring Profiles Based on Nonparametric Regression Methods. Technometrics, 50(4), 512-526. https://doi.org/10.1198/004017008000000433
