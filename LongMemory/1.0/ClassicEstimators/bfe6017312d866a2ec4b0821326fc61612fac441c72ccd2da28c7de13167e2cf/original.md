```
log_variance_est(x::Array; m::Int=200)
```

Computes the long memory estimate using the log-variance.

# Arguments

  * `x::Array`: The time series.

# Output

  * `d_var::Real`: The estimated long memory parameter computed as (beta+1)/2, where beta is the slope of the linear regression of the log-variance plot.

# Optional arguments

  * `m::Int`: The number of partitions of the time series. Default is 20. A value of m ≈ length(x)/2 is recommended.

# Notes

This function uses the linear regression method on the log-variance to estimate the long memory parameter.

# Examples

```julia
julia> log_variance_est(randn(100,1); m = 40)
```
