```
cycle_digraph(n)
```

Create a directed [cycle graph](https://en.wikipedia.org/wiki/Cycle_graph) with `n` vertices.

# Examples

```jldoctest
julia> cycle_digraph(3)
{3, 3} directed simple Int64 graph

julia> cycle_digraph(Int8(5))
{5, 5} directed simple Int8 graph
```
