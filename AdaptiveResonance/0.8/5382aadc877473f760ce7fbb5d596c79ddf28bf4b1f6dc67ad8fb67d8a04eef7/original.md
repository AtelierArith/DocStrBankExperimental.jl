```julia
DataConfig(
    mins::AbstractVector{T} where T<:Real,
    maxs::AbstractVector{T} where T<:Real
) -> AdaptiveResonance.DataConfig

```

# Summary

Convenience constructor for DataConfig, requiring only mins and maxs of the features.

This constructor is used when the mins and maxs differ across features. The dimension is inferred by the length of the mins and maxs.

# Arguments

  * `mins::RealVector`: a vector of minimum values for each feature dimension.
  * `maxs::RealVector`: a vector of maximum values for each feature dimension.

# Method List / Definition Locations

```julia
DataConfig(mins, maxs)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:79`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl).
