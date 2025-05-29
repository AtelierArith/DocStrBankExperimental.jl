```
LLCUSUM(x::AbstractMatrix, k::Real; ncuts::AbstractVector = [2 for _ in eachcol(x)])
```

A distibution-free Log-Linear CUSUM monitoring statistic based on data categorization.

# Fields

  * `k::Float64`: The allowance constant of the CUSUM statistic.
  * `value::Float64`: The initial value of the statistic (default: 0.0).
  * `Sobs::Vector{Float64}`: The vector of cumulative observed categories.
  * `Sexp::Vector{Float64}`: The vector of expected observed categories.
  * `qtls::Vector{Vector{Float64}}`: A vector of quantiles used for data categorization.
  * `f0::Vector{Float64}`: The vector of IC cell probabilities, estimated using a loglinear model.
  * `table::Matrix{Float64}`: The matrix of cell combinations.

# References

Qiu, P. (2008). Distribution-free multivariate process control based on log-linear modeling. IIE Transactions, 40(7), 664-677. https://doi.org/10.1080/07408170701744843
