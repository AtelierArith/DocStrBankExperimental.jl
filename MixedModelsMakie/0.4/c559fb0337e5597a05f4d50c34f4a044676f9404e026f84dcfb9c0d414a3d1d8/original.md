```
coefplot(x::Union{MixedModel,MixedModelBootstrap}; kwargs...)::Figure
coefplot!(fig::Union{GridLayoutBase.GridLayout, GridLayoutBase.GridPosition, GridLayoutBase.GridSubposition, Makie.Figure}, x::Union{MixedModel,MixedModelBootstrap};
          kwargs...)
coefplot!(ax::Axis, Union{MixedModel,MixedModelBootstrap};
          conf_level=0.95, vline_at_zero=true, show_intercept=true,
          scatter_attributes=(;),
          errorbars_attributes=(;),
          attributes...)
```

Create a coefficient plot of the fixed-effects and associated confidence intervals.

Inestimable coefficients (coefficients removed by pivoting in the rank deficient case) are excluded.

`attributes` are passed onto both `scatter!` and `errorbars!`, while `scatter_attributes` and `errorbars_attributes` are passed only onto `scatter!` and `errorbars!`, respectively. (Starting with Makie 0.21, unsupported attributes for a given plottype are no longer silently ignored, so it's necessary so separate out the attributes that are only valid for a single plot type.)

The mutating methods return the original object.

!!! note
    Inestimable coefficients (coefficients removed by pivoting in the rank deficient case) are excluded.

