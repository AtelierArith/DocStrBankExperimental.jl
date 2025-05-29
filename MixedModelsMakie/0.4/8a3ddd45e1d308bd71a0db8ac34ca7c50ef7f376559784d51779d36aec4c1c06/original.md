```
shrinkageplot(m::MixedModel, gf::Symbol=first(fnames(m)), θref, args...; kwargs...)
```

Return a scatter-plot matrix of the conditional means, b, of the random effects for grouping factor `gf`.

Two sets of conditional means are plotted: those at the estimated parameter values and those at `θref`. The default `θref` results in `Λ` being a very large multiple of the identity.  The corresponding conditional means can be regarded as unpenalized.

`args...` and `kwargs...` are passed on to [`shrinkageplot!`](@ref)
