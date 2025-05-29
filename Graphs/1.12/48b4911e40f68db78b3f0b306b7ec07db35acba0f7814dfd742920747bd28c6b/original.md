```
reverse(e)
```

Create a new edge from `e` with source and destination vertices reversed.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph(2);

julia> add_edge!(g, 1, 2);

julia> reverse(first(edges(g)))
Edge 2 => 1
```
