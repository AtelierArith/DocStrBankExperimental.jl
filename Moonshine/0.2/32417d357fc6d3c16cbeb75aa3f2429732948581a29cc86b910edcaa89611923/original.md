```
siblings(genealogy, v[, ωs])
siblings(genealogy, v[, ωs], buf_ptr)
```

Siblings of a vertex, that is the other vertices in the genealogy that share at least one parent, optionally restricted to a marginal genealogy.

A pointer to some kind of buffer (an array for instance) can be provided to avoid allocation. In that case, an `UnsafeArray` wrapped around it will be returned.

If you know in advance that `v` has a single sibling, you can use [`sibling`](@ref) instead.

See also [`child`](@ref), [`dad`](@ref), [`children`](@ref), [`dads`](@ref), [`descendants`](@ref) and [`ancestors`](@ref).

# Methods

```julia
siblings(genealogy, v, args)
```

defined at [`packages/Moonshine/7JVTP/src/Genealogy.jl:868`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl).
