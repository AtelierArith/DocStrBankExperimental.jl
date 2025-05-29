```
has_vertex(g, v)
```

Return true if `v` is a vertex of `g`.

# Examples

```jldoctest
julia> using Graphs

julia> has_vertex(SimpleGraph(2), 1)
true

julia> has_vertex(SimpleGraph(2), 3)
false
```
