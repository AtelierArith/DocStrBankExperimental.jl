```julia
sibling(genealogy, v)

```

Sibling of a vertex, that is the other vertex in the genealogy that have the same parent. It only makes sense to use this method if you know `v` has a single sibling. Otherwise use [`siblings`](@ref).

See also [`child`](@ref), [`dad`](@ref), [`children`](@ref), [`dads`](@ref), [`descendants`](@ref) and [`ancestors`](@ref).
