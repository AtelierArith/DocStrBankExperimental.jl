```
dst(e)
```

Return the destination vertex of edge `e`.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(2);

julia> add_edge!(g, 1, 2);

julia> dst(first(edges(g)))
2
```
