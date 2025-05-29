```julia
data_setup!(
    config::AdaptiveResonance.DataConfig,
    data::AbstractMatrix{T} where T<:Real
)

```

# Summary

Sets up the data config for the ART module before training.

This function crucially gets the original and complement-coded dimensions of the data, and it infers the bounds of the data (minimums and maximums) by the largest and smallest values along each feature dimension.

# Arguments

  * `config::DataConfig`: the ART/ARTMAP module's data configuration object.
  * `data::RealMatrix`: the 2-D batch of data to use for creating the data configuration.

# Method List / Definition Locations

```julia
data_setup!(config, data)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:268`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl).
