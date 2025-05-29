```julia
linear_normalization(
    data::AbstractVector{T} where T<:Real;
    config
) -> Vector{Float64}

```

# Summary

Normalize the data to the range [0, 1] along each feature.

# Arguments

  * `data::RealVector`: the 1-D sample of data to normalize.
  * `config::DataConfig=DataConfig()`: the data configuration from the ART/ARTMAP module.

# Method List / Definition Locations

```julia
linear_normalization(data; config)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:339`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl).
