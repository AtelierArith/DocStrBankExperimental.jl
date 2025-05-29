```
csa_forecast(x::Array, h::Int, p::Real, q::Real, σ::Real)
```

Computes the forecast of a long memory time series using the CSA method.

# Arguments

  * `x::Array`: The time series.
  * `h::Int`: The number of periods to forecast.
  * `p::Real`: The parameter p of the CSA process.
  * `q::Real`: The parameter q of the CSA process.
  * `σ::Real`: The standard deviation of the forecast errors.

# Output

  * `xfor::Array`: The forecast of the time series as a matrix where the first column is the forecast, the second column is the lower confidence band, and the third column is the upper confidence band. The first T elements are the original time series.

# Notes

Multiple dispatch is used to compute the forecast of a time series with or without confidence bands.

# Examples

```julia
julia> csa_forecast(csa_gen(100,1.4,1.4), 10, 1.4, 1.4, 1.0)
```
