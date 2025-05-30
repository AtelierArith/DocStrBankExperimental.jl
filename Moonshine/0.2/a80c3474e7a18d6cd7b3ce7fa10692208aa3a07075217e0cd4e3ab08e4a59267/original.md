```
ancestors(genealogy, v[, ωs])
ancestors(genealogy, v[, ωs], buf_ptr)
```

Ancestors of a vertex, optionally restricted to a marginal genealogy.

A pointer to some kind of buffer (an array for instance) can be provided to avoid allocation. In that case, an `UnsafeArray` wrapped around it will be returned.

The following rules are used to decide if an edge `e` is ancestral:

  * If ωs is a number, the ancestral interval of `e` must cover ωs.
  * If ωs is an Ω or a set of Ωs, the intersection of the ancestral interval of `e` with ωs must be non-empty.

See also [`child`](@ref), [`dad`](@ref), [`children`](@ref), [`dads`](@ref), [`sibling`](@ref), [`siblings`](@ref) and [`descendants`](@ref).

# Methods

```julia
ancestors(genealogy, v)
```

defined at [`packages/Moonshine/7JVTP/src/Genealogy.jl:777`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl).

```julia
ancestors(genealogy, v, ω)
```

defined at [`packages/Moonshine/7JVTP/src/Genealogy.jl:810`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl).
