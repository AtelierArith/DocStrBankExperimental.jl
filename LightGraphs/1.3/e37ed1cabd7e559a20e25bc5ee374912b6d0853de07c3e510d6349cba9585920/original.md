```
src(e)
```

Return the source vertex of edge `e`.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = SimpleGraph(2);

julia> add_edge!(g, 1, 2);

julia> src(first(edges(g)))
1
```
