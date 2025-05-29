```
ridgeplot(x::Union{MixedModel,MixedModelBootstrap}; kwargs...)::Figure
ridgeplot!(fig::Union{GridLayoutBase.GridLayout, GridLayoutBase.GridPosition, GridLayoutBase.GridSubposition, Makie.Figure}, x::Union{MixedModel,MixedModelBootstrap};
          kwargs...)
ridgeplot!(ax::Axis, Union{MixedModel,MixedModelBootstrap};
          conf_level=0.95, vline_at_zero=true, show_intercept=true,
          scatter_attributes=(;),
          errorbars_attributes=(;),
          band_attributes=(;),
          lines_attributes=(;),
          attributes...)
```

Create a ridge plot for the bootstrap samples of the fixed effects.

Densities are normalized so that the maximum density is always 1.

The highest density interval corresponding to `conf_level` is marked with a bar at the bottom of each density. Setting `conf_level=missing` removes the markings for the highest density interval.

`attributes` are passed onto [`coefplot`](@ref), `band!` and `lines!`. `scatter_attributes` and `errorbars_attributes` are passed only onto [`coefplot`](@ref). `band_attributes` and `lines_attributes` are passed only onto `band!` and `linesbars!`, respectively. (Starting with Makie 0.21, unsupported attributes for a given plottype are no longer silently ignored, so it's necessary so separate out the attributes that are only valid for a single plot type.)

The mutating methods return the original object.

!!! note
    Inestimable coefficients (coefficients removed by pivoting in the rank deficient case) are excluded.

