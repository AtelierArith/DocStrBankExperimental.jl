```
zerovector!!(x, [S::Type{<:Number} = scalartype(x)])
```

Construct a zero vector in the vector space of `x`, thereby trying to overwrite and thus recycle `x` when possible. Optionally, a modified scalar type `S` for the resulting zero vector can be specified.

!!! note
    New types should only implement the one-argument version. The two-argument version amounts to `S == scalartype(x) ? zerovector!!(x) : zerovector(x, S)`


Also see: [`zerovector`](@ref), [`zerovector!`](@ref)
