```
dads(genealogy, v[, ωs])
```

Parents of a vertex, optionally restricted to a marginal genealogy. If you know in advance that `v` has a single dad, use [̀̀`dad`](@ref) instead.

The following rules are used to decide if an edge `e` is ancestral:

  * If ωs is a number, the ancestral interval of `e` must cover ωs.
  * If ωs is an Ω or a set of Ωs, the intersection of the ancestral interval of `e` with ωs must be non-empty.

!!! danger
    Return a **reference** to the underlying adjacency lists. No touchy!


See also [`child`](@ref), [`children`](@ref), [`sibling`](@ref), [`siblings`](@ref), [`descendants`](@ref) and [`ancestors`](@ref).

# Methods

```julia
dads(arg, v, ωs)
dads(arg, v, ωs)
dads(arg, v, ωs)
```

defined at [`packages/Moonshine/7JVTP/src/Arg/Arg.jl:123`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Arg/Arg.jl).

```julia
dads(genealogy, v)
```

defined at [`packages/Moonshine/7JVTP/src/Genealogy.jl:700`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl).
