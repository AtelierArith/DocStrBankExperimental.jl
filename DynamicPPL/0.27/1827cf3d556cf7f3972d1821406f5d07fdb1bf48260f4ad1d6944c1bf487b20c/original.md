```
link([t::AbstractTransformation, ]vi::AbstractVarInfo, model::Model)
link([t::AbstractTransformation, ]vi::AbstractVarInfo, spl::AbstractSampler, model::Model)
```

Transform the variables in `vi` to their linked space without mutating `vi`, using the transformation `t`. 

If `t` is not provided, `default_transformation(model, vi)` will be used.

See also: [`default_transformation`](@ref), [`invlink`](@ref).
