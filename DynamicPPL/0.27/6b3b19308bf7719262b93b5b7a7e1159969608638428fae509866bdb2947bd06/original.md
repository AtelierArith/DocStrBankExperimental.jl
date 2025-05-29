```
invlink([t::AbstractTransformation, ]vi::AbstractVarInfo, model::Model)
invlink([t::AbstractTransformation, ]vi::AbstractVarInfo, spl::AbstractSampler, model::Model)
```

Transform the variables in `vi` to their constrained space without mutating `vi`, using the (inverse of) transformation `t`.

If `t` is not provided, `default_transformation(model, vi)` will be used.

See also: [`default_transformation`](@ref), [`link`](@ref).
