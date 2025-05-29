```
complete_digraph(n)
```

Create a directed [complete graph](https://en.wikipedia.org/wiki/Complete_graph) with `n` vertices.

# Examples

```jldoctest
julia> using Graphs

julia> complete_digraph(5)
{5, 20} directed simple Int64 graph

julia> complete_digraph(Int8(6))
{6, 30} directed simple Int8 graph
```
