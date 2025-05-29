```
path_graph(n)
```

Create an undirected [path graph](https://en.wikipedia.org/wiki/Path_graph) with `n` vertices.

# Examples

```jldoctest
julia> using Graphs

julia> path_graph(5)
{5, 4} undirected simple Int64 graph

julia> path_graph(Int8(10))
{10, 9} undirected simple Int8 graph
```
