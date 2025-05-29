```
outneighbors(g, v)
```

Return a list of all neighbors connected to vertex `v` by an outgoing edge.

# Implementation Notes

Returns a reference to the current graph's internal structures, not a copy. Do not modify result. If the graph is modified, the behavior is undefined: the array behind this reference may be modified too, but this is not guaranteed.

# Examples

```jldoctest
julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> outneighbors(g, 4)
1-element Array{Int64,1}:
 5
```
