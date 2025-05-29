```
ridge2d(bs::MixedModelBootstrap; ptype=:β, kwargs...)
ridge2d!(f::Union{GridLayoutBase.GridLayout, GridLayoutBase.GridPosition, GridLayoutBase.GridSubposition, Makie.Figure}, bs::MixedModelBootstrap; ptype=:β)
```

Plot pairwise bivariate scatter plots with overlain densities for a bootstrap sample.

`ptype` specifies the set of parameters to examine, e.g. `:β`, `:σ`, `:ρ`.

The mutating methods return the original object.
