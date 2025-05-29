```
wheel_digraph(n)
```

Create a directed [wheel graph](https://en.wikipedia.org/wiki/Wheel_graph) with `n` vertices.

# Examples

```jldoctest
julia> wheel_digraph(5)
{5, 8} directed simple Int64 graph

julia> wheel_digraph(Int8(6))
{6, 10} directed simple Int8 graph
```
