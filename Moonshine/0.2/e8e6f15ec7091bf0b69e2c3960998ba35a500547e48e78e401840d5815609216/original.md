```
children(genealogy, v[, ωs])
```

Children of a vertex, optionally restricted to a marginal genealogy. If you know in advance that `v` has a single child, use [̀̀`child`](@ref) instead.

The following rules are used to decide if an edge `e` is ancestral:

  * If ωs is a number, the ancestral interval of `e` must cover ωs.
  * If ωs is an Ω or a set of Ωs, the intersection of the ancestral interval of `e` with ωs must be non-empty.

!!! danger
    Return a **reference** to the underlying adjacency lists. No touchy!


See also [`dad`](@ref), [`dads`](@ref), [`sibling`](@ref), [`siblings`](@ref), [`descendants`](@ref) and [`ancestors`](@ref).

# Methods

```julia
children(arg, v, ωs)
children(arg, v, ωs)
children(arg, v, ωs)
```

defined at [`packages/Moonshine/7JVTP/src/Arg/Arg.jl:123`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Arg/Arg.jl).

```julia
children(genealogy, v)
```

defined at [`packages/Moonshine/7JVTP/src/Genealogy.jl:700`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl).
