```
complete_graph(n)
```

Create an undirected [complete graph](https://en.wikipedia.org/wiki/Complete_graph) with `n` vertices.

# Examples

```jldoctest
julia> complete_graph(5)
{5, 10} undirected simple Int64 graph

julia> complete_graph(Int8(6))
{6, 15} undirected simple Int8 graph
```
