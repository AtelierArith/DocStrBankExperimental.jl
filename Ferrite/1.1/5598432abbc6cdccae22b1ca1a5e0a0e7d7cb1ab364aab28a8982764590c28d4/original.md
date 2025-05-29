```
getnodes(grid::AbstractGrid)
getnodes(grid::AbstractGrid, v::Union{Int,Vector{Int}}
getnodes(grid::AbstractGrid, setname::String)
```

Returns either all `nodes::Collection{N}` of a `<:AbstractGrid` or a subset based on an `Int`, `Vector{Int}` or `String`. The last option tries to call a `nodeset` of the `<:AbstractGrid`. `Collection{N}` refers to some indexable collection where each element corresponds to a Node.
