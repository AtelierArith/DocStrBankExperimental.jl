```
add_vertices!(g, n)
```

Add `n` new vertices to the graph `g`. Return the number of vertices that were added successfully.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleGraph()
{0, 0} undirected simple Int64 graph

julia> add_vertices!(g, 2)
2
```
