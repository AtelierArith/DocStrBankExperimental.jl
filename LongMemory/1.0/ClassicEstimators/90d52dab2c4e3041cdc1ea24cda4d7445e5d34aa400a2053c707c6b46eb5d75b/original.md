```
autocovariance(x::Array, k::Int)
```

Computes the autocovariance of a time series.

# Arguments

  * `x::Array`: The time series.
  * `k::Int`: The lag of the autocovariance.

# Output

  * `acv::Array`: The autocovariance.

# Examples

```julia
julia> autocovariance(randn(100), 2)
```
