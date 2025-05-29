```
plot_changes_significance(res, signif) → (fig, axs)
```

Return `fig::Figure` and `axs::Matrix{Axis}`, on which `res::ChangesResults` and `signif::SurrogatesSignificance` have been visualised. The source code is as simple as:

```julia
fig, axs = plot_indicator_changes(res; kwargs...)
plot_significance!(axs, res, signif; kwargs...)
```

For more information, refer to [`plot_indicator_changes`](@ref) and [`plot_significance!`](@ref).
