```
lollipop_graph(n1, n2)
```

Create a [lollipop graph](https://en.wikipedia.org/wiki/Lollipop_graph) consisting of a clique of size `n1` connected by an edge to a path of size `n2`.

### Implementation Notes

Preserves the eltype of `n1` and `n2`. Will error if the required number of vertices exceeds the eltype. `n1` and `n2` must be at least 1 so that both the clique and the path have at least one vertex. The graph is organized with nodes `1:n1` being the clique and `n1+1:n1+n2` being the path. The clique is connected to the path by an edge `(n1, n1+1)`.

# Examples

```jldoctest
julia> using Graphs

julia> lollipop_graph(2, 5)
{7, 6} undirected simple Int64 graph

julia> lollipop_graph(Int8(3), Int8(4))
{7, 7} undirected simple Int8 graph
```
