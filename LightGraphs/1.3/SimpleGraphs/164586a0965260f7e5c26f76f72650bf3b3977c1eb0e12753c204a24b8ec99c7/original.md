```
ladder_graph(n)
```

Create a [ladder graph](https://en.wikipedia.org/wiki/Ladder_graph) consisting of `2n` nodes and `3n-2` edges.

### Implementation Notes

Preserves the eltype of `n`. Will error if the required number of vertices exceeds the eltype.

# Examples

```jldoctest
julia> ladder_graph(3)
{6, 7} undirected simple Int64 graph

julia> ladder_graph(Int8(4))
{8, 10} undirected simple Int8 graph
```
