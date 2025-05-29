```
star_graph(n)
```

Create an undirected [star graph](https://en.wikipedia.org/wiki/Star_(graph_theory)) with `n` vertices.

# Examples

```jldoctest
julia> star_graph(3)
{3, 2} undirected simple Int64 graph

julia> star_graph(Int8(10))
{10, 9} undirected simple Int8 graph
```
