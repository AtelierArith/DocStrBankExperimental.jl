```
complete_bipartite_graph(n1, n2)
```

Create an undirected [complete bipartite graph](https://en.wikipedia.org/wiki/Complete_bipartite_graph) with `n1 + n2` vertices.

# Examples

```jldoctest
julia> using Graphs

julia> complete_bipartite_graph(3, 4)
{7, 12} undirected simple Int64 graph

julia> complete_bipartite_graph(Int8(3), Int8(4))
{7, 12} undirected simple Int8 graph
```
