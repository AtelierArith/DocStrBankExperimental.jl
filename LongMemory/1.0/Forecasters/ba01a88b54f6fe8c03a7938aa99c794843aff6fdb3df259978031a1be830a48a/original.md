```
fi_forecast(x::Array, h::Int, d::Real, σ::Real)
```

Computes the forecast of a long memory time series using the fractional differencing method.

# Arguments

  * `x::Array`: The time series.
  * `h::Int`: The number of periods to forecast.
  * `d::Real`: The fractional differencing parameter.
  * `σ::Real`: The standard deviation of the forecast errors.

# Output

  * `xfor::Array`: The forecast of the time series as a matrix where the first column is the forecast, the second column is the lower confidence band, and the third column is the upper confidence band. The first T elements are the original time series.

# Notes

Multiple dispatch is used to compute the forecast of a time series with or without confidence bands.

# Examples

```julia
julia> fi_forecast(fi_gen(100,0.2), 10, 0.2)
```
