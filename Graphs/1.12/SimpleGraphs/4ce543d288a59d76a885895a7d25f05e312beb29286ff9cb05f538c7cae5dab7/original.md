```
circular_ladder_graph(n)
```

Create a [circular ladder graph](https://en.wikipedia.org/wiki/Ladder_graph#Circular_ladder_graph) consisting of `2n` nodes and `3n` edges. This is also known as the [prism graph](https://en.wikipedia.org/wiki/Prism_graph).

### Implementation Notes

Preserves the eltype of the partitions vector. Will error if the required number of vertices exceeds the eltype. `n` must be at least 3 to avoid self-loops and multi-edges.

# Examples

```jldoctest
julia> using Graphs

julia> circular_ladder_graph(3)
{6, 9} undirected simple Int64 graph

julia> circular_ladder_graph(Int8(4))
{8, 12} undirected simple Int8 graph
```
