```
@delete obj_optic
```

Define an optic and call [`delete`](@ref) on it.

```jldoctest
julia> using Accessors

julia> xs = (1,2,3);

julia> ys = @delete xs[2]
(1, 3)
```

Supports the same syntax as [`@optic`](@ref). See also [`@set`](@ref).
