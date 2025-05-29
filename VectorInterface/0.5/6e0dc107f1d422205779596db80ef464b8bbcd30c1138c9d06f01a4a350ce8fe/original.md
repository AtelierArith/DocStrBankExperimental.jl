```
zerovector(x, [S::Type{<:Number} = scalartype(x)])
```

Returns a zero vector in the vector space of `x`. Optionally, a modified scalar type `S` for the resulting zero vector can be specified.

!!! note
    New types should only implement the two-argument version, if applicable.


Also see: [`zerovector!`](@ref), [`zerovector!!`](@ref)
