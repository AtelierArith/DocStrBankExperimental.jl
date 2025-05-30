```
plot_changes_significance(res, signif) → (fig, axs)
```

`fig::Figure` と `axs::Matrix{Axis}` を返します。これには `res::ChangesResults` と `signif::SurrogatesSignificance` が視覚化されています。ソースコードは次のようにシンプルです：

```julia
fig, axs = plot_indicator_changes(res; kwargs...)
plot_significance!(axs, res, signif; kwargs...)
```

詳細については、[`plot_indicator_changes`](@ref) と [`plot_significance!`](@ref) を参照してください。
