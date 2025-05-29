```
fi_forecast_plot(x::Array, h::Int, d::Real)
```

Plots the forecast of a long memory time series using the fractional differencing method.

# Arguments

  * `x::Array`: The time series.
  * `h::Int`: The number of periods to forecast.
  * `d::Real`: The fractional differencing parameter.

# Output

  * `p1::Plot`: The plot of the original time series and the forecast.

# Notes

Multiple dispatch is used to plot the forecast of a time series with or without confidence bands. Plotting is done by calling the `fi_forecast` function.

# Examples

```julia
julia> fi_forecast_plot(fi_gen(100,0.2), 10, 0.2)
```
