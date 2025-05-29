```julia
complement_code(
    data::AbstractArray{T} where T<:Real;
    config
) -> Any

```

# Summary

Normalizes the data x to [0, 1] and returns the augmented vector [x, 1 - x].

# Arguments

  * `data::RealArray`: the 1-D or 2-D data to be complement coded.
  * `config::DataConfig=DataConfig()`: the data configuration for the ART/ARTMAP module.

# Method List / Definition Locations

```julia
complement_code(data; config)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:402`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl).
