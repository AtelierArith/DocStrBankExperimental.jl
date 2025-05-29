```
path_digraph(n)
```

Creates a directed [path graph](https://en.wikipedia.org/wiki/Path_graph) with `n` vertices.

# Examples

```jldoctest
julia> path_digraph(5)
{5, 4} directed simple Int64 graph

julia> path_digraph(Int8(10))
{10, 9} directed simple Int8 graph
```
