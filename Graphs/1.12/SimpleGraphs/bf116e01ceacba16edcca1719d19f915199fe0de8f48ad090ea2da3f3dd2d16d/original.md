```
wheel_graph(n)
```

Create an undirected [wheel graph](https://en.wikipedia.org/wiki/Wheel_graph) with `n` vertices.

# Examples

```jldoctest
julia> using Graphs

julia> wheel_graph(5)
{5, 8} undirected simple Int64 graph

julia> wheel_graph(Int8(6))
{6, 10} undirected simple Int8 graph
```
