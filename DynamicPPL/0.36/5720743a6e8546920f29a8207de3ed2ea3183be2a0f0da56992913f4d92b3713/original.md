```
istrans(vi::AbstractVarInfo[, vns::Union{VarName, AbstractVector{<:Varname}}])
```

Return `true` if `vi` is working in unconstrained space, and `false` if `vi` is assuming realizations to be in support of the corresponding distributions.

If `vns` is provided, then only check if this/these varname(s) are transformed.

!!! warning
    Not all implementations of `AbstractVarInfo` support transforming only a subset of the variables.

