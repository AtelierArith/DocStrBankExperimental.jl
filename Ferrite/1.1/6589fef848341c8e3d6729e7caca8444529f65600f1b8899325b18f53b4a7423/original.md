```
getcells(grid::AbstractGrid)
getcells(grid::AbstractGrid, v::Union{Int,Vector{Int}}
getcells(grid::AbstractGrid, setname::String)
```

Returns either all `cells::Collection{C<:AbstractCell}` of a `<:AbstractGrid` or a subset based on an `Int`, `Vector{Int}` or `String`. Whereas the last option tries to call a `cellset` of the `grid`. `Collection` can be any indexable type, for `Grid` it is `Vector{C<:AbstractCell}`.
