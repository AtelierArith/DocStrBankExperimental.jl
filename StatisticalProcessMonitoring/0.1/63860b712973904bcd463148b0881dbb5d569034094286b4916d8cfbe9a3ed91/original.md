```
LLD(x::AbstractMatrix, l::Real; ncuts::AbstractVector = [3 for _ in eachcol(x)], N = 1)
```

A Log-Linear Directional monitoring statistic based on data categorization.

# Fields

  * `l::Float64`: The exponentially weighted smoothing constant of the statistic.
  * `value::Float64`: The initial value of the statistic (default: 0.0).
  * `qtls::Vector{Vector{Float64}}`: A vector of quantiles used for data categorization.
  * `f0::Vector{Float64}`: The vector of IC cell probabilities, estimated using a loglinear model.
  * `table::Matrix{Float64}`: The matrix of cell combinations.
  * `Sigma::Matrix{Float64}`: The covariance matrix of the cell counts.
  * `directions::Matrix{Float64}`: The matrix of directions to be used in the hypohesis test (see Equation (6) of [Li, 2012]). This is calculated according to the procedure described in Equations (5) and (6) of [Wang, 2017].
  * `N::Int`: The number of observations at each time point (default: 1)
  * `z_k::Vector{Float64}`: The current vector of smoothed values.

# References

Li, J., Tsung, F., & Zou, C. (2012). Directional Control Schemes for Multivariate Categorical Processes. Journal of Quality Technology, 44(2), 136â€“154. https://doi.org/10.1080/00224065.2012.11917889

Wang, J., Li, J., & Su, Q. (2017). Multivariate Ordinal Categorical Process Control Based on Log-Linear Modeling. Journal of Quality Technology, 49(2), 108-122. https://doi.org/10.1080/00224065.2017.11917983
