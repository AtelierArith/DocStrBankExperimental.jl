```julia
get_data_characteristics(
    data::AbstractMatrix{T} where T<:Real;
    config
) -> NTuple{4, Any}

```

# Summary

Get the characteristics of the data, taking account if a data config is passed.

If no DataConfig is passed, then the data characteristics come from the array itself. Otherwise, use the config for the statistics of the data and the data array for the number of samples.

# Arguments

  * `data::RealMatrix`: the 2-D data to be complement coded.
  * `config::DataConfig=DataConfig()`: the data configuration for the ART/ARTMAP module.

# Method List / Definition Locations

```julia
get_data_characteristics(data; config)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:310`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl).
