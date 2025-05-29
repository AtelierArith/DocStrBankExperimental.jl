```
rescaled_range_est(x::Array; k::Int = 20)
```

Estimates the long memory parameter of a time series using the rescaled range (R/S) statistic.

# Arguments

  * `x::Array`: The time series.

# Output

  * `d::Real`: The estimated long memory parameter.

# Optional arguments

  * `k::Int`: The number of partitions of the time series. Default is 20.

# Notes

This function uses the linear regression method on the log of the rescaled range to estimate the long memory parameter. The Hurst coefficient is related to the long memory parameter d by the formula H = d + 1/2.

# Examples

```julia
julia> rescaled_range_est(randn(100))
```
