```
caterpillar!(f::Indexable, r::RanefInfo;
            orderby=1, cols::Union{Nothing,AbstractVector}=nothing,
            dotcolor=(:red, 0.2), barcolor=:black,
            vline_at_zero::Bool=false)
caterpillar!(f::Indexable, m::MixedModel,
             gf::Symbol=first(fnames(m)); orderby=1,
             cols::Union{Nothing,AbstractVector}=nothing,
             dotcolor=(:red, 0.2), barcolor=:black,
             vline_at_zero::Bool=false)
```

Add Axes of a caterpillar plot from `r` to `f`.

When passing a `MixedModel`, `gf` specifies which grouping variable is displayed. Alternatively, [`ranefinfo`](@ref) may be used to construct the [`RanefInfo`](@ref) object directly. Constructing `RanefInfo` directly can be used to avoid re-computing the conditional variances.

The order of the levels on the vertical axes is increasing `orderby` column of `r.ranef`, usually the `(Intercept)` random effects. Setting `orderby=nothing` will disable sorting, i.e. return the levels in the order they are stored in.

The display can be restricted to a subset of random effects associated with a grouping variable by specifying `cols`, either by indices or term names.

!!! note
    Even when not sorting the levels, they might have already been sorted during model matrix construction. If you want impose a particular ordering on the levels, then you must sort the relevant fields in the `RanefInfo` object before calling `caterpillar!`.


!!! note
    `orderby` is the $n$th column of the columns specified by `cols`.

