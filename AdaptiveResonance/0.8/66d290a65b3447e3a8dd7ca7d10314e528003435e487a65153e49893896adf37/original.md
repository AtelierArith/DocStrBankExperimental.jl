```julia
linear_normalization(
    data::AbstractMatrix{T} where T<:Real;
    config
) -> Any

```

# Summary

Normalize the data to the range [0, 1] along each feature.

# Arguments

  * `data::RealMatrix`: the 2-D batch of data to normalize.
  * `config::DataConfig=DataConfig()`: the data configuration from the ART/ARTMAP module.

# Method List / Definition Locations

```julia
linear_normalization(data; config)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:369`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl).
