```julia
data_setup!(
    art::AdaptiveResonance.ARTModule,
    data::AbstractMatrix{T} where T<:Real
)

```

# Summary

Convenience method for setting up the DataConfig of an ART module in advance.

# Arguments

  * `art::ARTModule`: the ART/ARTMAP module to manually configure the data config for.
  * `data::RealArray`: the 2-D batch of data used to create the data config.

# Method List / Definition Locations

```julia
data_setup!(art, data)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:295`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl).
