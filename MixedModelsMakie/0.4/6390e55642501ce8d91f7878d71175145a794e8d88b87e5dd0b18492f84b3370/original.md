```
qqcaterpillar!(f::Indexable, r::RanefInfo;
               cols::Union{Nothing,AbstractVector}=nothing,
               dotcolor=(:red, 0.2), barcolor=:black)
qqcaterpillar!(f::Indexable, m::MixedModel,
               gf::Symbol=first(fnames(m));
               cols::Union{Nothing,AbstractVector}=nothing,
               dotcolor=(:red, 0.2), barcolor=:black,
               vline_at_zero::Bool=false)
```

Update the figure with a caterpillar plot with the vertical axis on the Normal() quantile scale.

When passing a `MixedModel`, `gf` specifies which grouping variable is displayed. Alternatively, [`ranefinfo`](@ref) may be used to construct the [`RanefInfo`](@ref) object directly. Constructing `RanefInfo` directly can be used to avoid re-computing the conditional variances.

The display can be restricted to a subset of random effects associated with a grouping variable by specifying `cols`, either by indices or term names.

The order of the levels on the vertical axes is increasing `orderby` column of `r.ranef`, usually the `(Intercept)` random effects. Setting `orderby=nothing` will disable sorting, i.e. return the levels in the order they are stored in.
