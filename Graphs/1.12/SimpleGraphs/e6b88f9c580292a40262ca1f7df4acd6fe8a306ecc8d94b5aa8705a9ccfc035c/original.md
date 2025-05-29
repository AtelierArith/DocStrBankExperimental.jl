```
cycle_graph(n)
```

Create an undirected [cycle graph](https://en.wikipedia.org/wiki/Cycle_graph) with `n` vertices.

# Examples

```jldoctest
julia> using Graphs

julia> cycle_graph(3)
{3, 3} undirected simple Int64 graph

julia> cycle_graph(Int8(5))
{5, 5} undirected simple Int8 graph
```
