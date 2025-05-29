```
rescaled_range(x::Array; k::Int = 20)
```

Computes the rescaled range (R/S) statistic of a time series.

# Arguments

  * `x::Array`: The time series.

# Optional arguments

  * `k::Int`: The number of partitions of the time series. Default is 20.

# Output

  * `RS::Array`: The rescaled range statistic.

# Examples

```julia
julia> rescaled_range(randn(100))
```
