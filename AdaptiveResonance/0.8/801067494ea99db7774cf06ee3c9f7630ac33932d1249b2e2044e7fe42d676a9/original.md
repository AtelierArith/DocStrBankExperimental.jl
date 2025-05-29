```julia
performance(
    y_hat::AbstractVector{T} where T<:Integer,
    y::AbstractVector{T} where T<:Integer
) -> Any

```

# Summary

Convenience function to get the categorization performance of y_hat against y.

# Arguments

  * `y_hat::IntegerVector`: the estimated labels.
  * `y::IntegerVector`: the true labels.

# Method List / Definition Locations

```julia
performance(y_hat, y)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:200`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl).
