```
log_variance_plot(x::Array; m::Int=100, slope::Bool=false, slope2::Bool=false)
```

Produces the log-variance plot of a time series.

# Arguments

  * `x::Array`: The time series.

# Output

  * `d_var::Real`: The estimated long memory parameter computed as (beta+1)/2, where beta is the slope of the linear regression of the log of the variance plot.

# Optional arguments

  * `m::Int`: The number of partitions of the time series. Default is 20. A value of m ≈ length(x)/2 is recommended.
  * `slope::Bool`: If true, the slope of the linear regression is displayed.
  * `slope2::Bool`: If true, the theoretical slope for a short memory process is displayed.

# Notes

This function uses the linear regression method on the log of the variance plot to estimate the long memory parameter.

# Examples

```julia
julia> log_variance_plot(randn(100,1); m = 40)
```
