```julia
DataConfig(
    data::AbstractMatrix{T} where T<:Real
) -> AdaptiveResonance.DataConfig

```

# Summary

Convenience constructor for DataConfig, requiring only the data matrix.

# Arguments

  * `data::RealMatrix`: the 2-D batch of data to be used for inferring the data configuration.

# Method List / Definition Locations

```julia
DataConfig(data)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:120`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl).
