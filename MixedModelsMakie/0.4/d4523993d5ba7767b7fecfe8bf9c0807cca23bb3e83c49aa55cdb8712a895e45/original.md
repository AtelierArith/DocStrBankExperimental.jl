```
shrinkageplot!(f::Indexable, m::MixedModel,
               gf::Symbol=first(fnames(m)), θref;
               ellipse=false, ellipse_scale=1, n_ellipse=5,
               cols::Union{Nothing,AbstractVector}=nothing,
               shrunk_dotcolor=(:blue, 0.25), ref_dotcolor=(:red, 0.25),
               ellipse_color=:green, ellipse_linestyle=:dash)
```

Return a scatter-plot matrix of the conditional means, b, of the random effects for grouping factor `gf`.

Two sets of conditional means are plotted: those at the estimated parameter values and those at `θref`. The default `θref` results in `Λ` being a very large multiple of the identity.  The corresponding conditional means can be regarded as unpenalized.

The display can be restricted to a subset of random effects associated with a grouping variable by specifying `cols`, either by indices or term names.

Correlation ellipses can be added with `ellipse=true`, with the number of ellipses controlled by `n_ellipse`. The ellipses are equally spaced between the outer ellipse and the origin (center). The scaling of the ellipses can be adjusted with the multiplicative `ellipse_scale`. If you are unable to see the ellipses, try increasing `ellipse_scale`.

!!! note
    For degenerate (singular) models, the correlation ellipse will also be degenerate, i.e., collapse to a point or line.

