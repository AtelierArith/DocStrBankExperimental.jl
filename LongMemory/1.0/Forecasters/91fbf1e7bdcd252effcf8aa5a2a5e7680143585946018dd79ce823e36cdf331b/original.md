```
har_forecast(x::Array, h::Int; flag::Bool = false, m::Array=[1,5,22])
```

Computes the forecast of a time series by fitting and recursevely forecasting the HAR model.

# Arguments

  * `x::Array`: The time series.
  * `h::Int`: The number of periods to forecast.

# Output

  * `xfor::Array`: The forecast of the time series. The first T-max(m) elements are the original time series.

# Optional Arguments

  * `flag::Bool`: If true, the output is a matrix where the first column is the forecast, the second column is the lower confidence band, and the third column is the upper confidence band. The default is false.
  * `m::Array`: The lags to include in the HAR model. The default is [1,5,22].

# Examples

```julia
julia> har_forecast(fi_gen(100,0.2), 10)
```
