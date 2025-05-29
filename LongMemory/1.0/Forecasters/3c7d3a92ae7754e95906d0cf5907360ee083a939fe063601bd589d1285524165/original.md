```
har_forecast_plot(x::Array, h::Int; flag::Bool = true, m::Array=[1,5,22])
```

Plots the forecast of a time series by fitting and recursevely forecasting the HAR model.

# Arguments

  * `x::Array`: The time series.
  * `h::Int`: The number of periods to forecast.

# Output

  * `p1::Plot`: The plot of the original time series and the forecast.

# Optional Arguments

  * `flag::Bool`: If true, the output is a matrix where the first column is the forecast, the second column is the lower confidence band, and the third column is the upper confidence band. The default is true.
  * `m::Array`: The lags to include in the HAR model. The default is [1,5,22].

# Notes

Multiple dispatch is used to plot the forecast of a time series with or without confidence bands. Plotting is done by calling the `har_forecast` function.

# Examples

```julia
julia> har_forecast_plot(figen(100,0.2), 10)
```
