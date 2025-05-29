```
complete_multipartite_graph(partitions)
```

Create an undirected [complete bipartite graph](https://en.wikipedia.org/wiki/Complete_bipartite_graph) with `sum(partitions)` vertices. A partition with `0` vertices is skipped.

### Implementation Notes

Preserves the eltype of the partitions vector. Will error if the required number of vertices exceeds the eltype.

# Examples

```jldoctest
julia> using Graphs

julia> complete_multipartite_graph([1,2,3])
{6, 11} undirected simple Int64 graph

julia> complete_multipartite_graph(Int8[5,5,5])
{15, 75} undirected simple Int8 graph
```
