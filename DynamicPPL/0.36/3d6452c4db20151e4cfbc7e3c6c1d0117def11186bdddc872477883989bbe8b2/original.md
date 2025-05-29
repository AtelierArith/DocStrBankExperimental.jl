```
link!!([t::AbstractTransformation, ]vi::AbstractVarInfo, model::Model)
link!!([t::AbstractTransformation, ]vi::AbstractVarInfo, vns::NTuple{N,VarName}, model::Model)
```

Transform variables in `vi` to their linked space, mutating `vi` if possible.

Either transform all variables, or only ones specified in `vns`.

Use the  transformation `t`, or `default_transformation(model, vi)` if one is not provided.

See also: [`default_transformation`](@ref), [`invlink!!`](@ref).
