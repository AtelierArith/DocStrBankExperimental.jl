```julia
DataConfig(
    min::Real,
    max::Real,
    dim::Integer
) -> AdaptiveResonance.DataConfig

```

# Summary

Convenience constructor for DataConfig, requiring only a global min, max, and dim.

This constructor is used in the case that the feature mins and maxs are all the same respectively.

# Arguments

  * `min::Real`: the minimum value across all features.
  * `max::Real`: the maximum value across all features.
  * `dim::Integer`: the dimension of the features, which must be provided because it cannot be inferred from just the minimum or maximum values.

# Method List / Definition Locations

```julia
DataConfig(min, max, dim)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:104`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl).
