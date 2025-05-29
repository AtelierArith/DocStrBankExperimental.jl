```
linreg(x, y)
```

Linear regression between two vectors.

# Arguments

  * `x::AbstractVector`
  * `y::AbstractVector`

# Notes

To predict, use: `new*x = DataFrame(x = [3.5, 7]); predict(lr, new*x)

# Returns

Named tuple containing:

  * `lr::StatsModels.TableRegressionModel`: model
  * `c::Vector{Float64}`: coefficients
  * `se::Vector{Float64}`: standard error for coefficients
  * `R2::Float64`: R²
  * `R2adj::Float64`: R² adjusted
  * `aic::Float64`:: Akaike’s Information Criterion (AIC)
  * `bic::Float64`:: Bayesian Information Criterion (BIC)
  * `lf::Vector{Float64}`: linear fit (plot(x, lf))
