```
clique_graph(k, n)
```

Create a graph consisting of `n` connected `k`-cliques.

# Examples

```jldoctest
julia> clique_graph(4, 10)
{40, 70} undirected simple Int64 graph

julia> clique_graph(Int8(10), Int8(4))
{40, 184} undirected simple Int8 graph
```
