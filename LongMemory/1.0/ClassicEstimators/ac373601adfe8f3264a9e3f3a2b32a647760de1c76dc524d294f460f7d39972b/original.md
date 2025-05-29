```
rescaled_range_plot(x::Array; k::Int = 100, slope::Bool = false, slope2::Bool = false)
```

Produces the rescaled range plot of a time series.

# Arguments

  * `x::Array`: The time series.

# Output

  * `p1::Plots.Plot`: The rescaled range plot.

# Optional arguments

  * `k::Int`: The number of partitions of the time series. Default is 100.
  * `slope::Bool`: If true, the slope of the linear regression is displayed.
  * `slope2::Bool`: If true, the theoretical slope for a short memory process is displayed.

# Notes

This function uses the linear regression method on the log of the rescaled range to estimate the long memory parameter. The Hurst coefficient is related to the long memory parameter d by the formula H = d + 1/2.

# Examples

```julia
julia> rescaled_range_plot(randn(300,1))
```
