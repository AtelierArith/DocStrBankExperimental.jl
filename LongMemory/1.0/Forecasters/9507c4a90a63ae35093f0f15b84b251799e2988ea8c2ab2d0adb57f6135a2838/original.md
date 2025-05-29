```
csa_forecast_plot(x::Array, h::Int, p::Real, q::Real)
```

Plots the forecast of a long memory time series using the CSA method.

# Arguments

  * `x::Array`: The time series.
  * `h::Int`: The number of periods to forecast.
  * `p::Real`: The parameter p of the CSA process.
  * `q::Real`: The parameter q of the CSA process.

# Output

  * `p1::Plot`: The plot of the original time series and the forecast.

# Notes

Multiple dispatch is used to plot the forecast of a time series with or without confidence bands. Plotting is done by calling the `csa_forecast` function.

# Examples

```julia
julia> csa_forecast_plot(csa_gen(100,1.4,1.4), 10, 1.4, 1.4)
```
