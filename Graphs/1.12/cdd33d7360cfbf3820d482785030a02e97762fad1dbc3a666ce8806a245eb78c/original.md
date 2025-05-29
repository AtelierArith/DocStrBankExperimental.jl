```
is_ordered(e)
```

Return true if the source vertex of edge `e` is less than or equal to the destination vertex.

# Examples

```jldoctest
julia> using Graphs

julia> g = DiGraph(2);

julia> add_edge!(g, 2, 1);

julia> is_ordered(first(edges(g)))
false
```
