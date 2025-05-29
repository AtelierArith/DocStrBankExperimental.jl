```
csa_forecast(x::Array, h::Int, p::Real, q::Real)
```

Computes the forecast of a long memory time series using the CSA method.

# Arguments

  * `x::Array`: The time series.
  * `h::Int`: The number of periods to forecast.
  * `p::Real`: The parameter p of the CSA process.
  * `q::Real`: The parameter q of the CSA process.

# Output

  * `xfor::Array`: The forecast of the time series as a column vector. The first T elements are the original time series.

# Notes

Multiple dispatch is used to compute the forecast of a time series with or without confidence bands.

# Examples

```julia
julia> csa_forecast(csa_gen(100,1.4,1.4), 10, 1.4, 1.4)
```
