```
split_catenation(graph::PeriodicGraph{N}) where N
```

Return a list of tuples `(subgraph, vmaps, mat, dim)` where `subgraph` is a connected component of the input `graph`. Each sublist `vmap` in `vmaps` is a distinct mapping of the vertices of the graph into those of the corresponding `subgraph`. The union of all the vertices in all the `vmaps`, repeated with the according periodicity, exactly covers all the vertices of the input graph, without repetition. `dim` is the [`dimensionality`](@ref) of these connected components, and `mat` is the transformation matrix between the input cell and the component's cell.

Each sublist contains connected components that share the same vertex indices.

## Example

```jldoctest
julia> g = PeriodicGraph("2    1 1  3 0   1 1  0 1   2 3  1 0   3 2  1 0");

julia> dimensionality(g)
Dict{Int64, Vector{Tuple{Vector{Int64}, Int64}}} with 2 entries:
  2 => [([1], 3)]
  1 => [([2, 3], 2)]

julia> splits = split_catenation(g);

julia> last.(splits) # One 2-dimensional catenation (vertex 1), one 1-dimensional (vertices 2 and 3)
2-element Vector{Int64}:
 2
 1

julia> subgraph, vmaps, mat, dim = last(splits);  # the 1-dimensional connected components

julia> vmaps  # first sublist takes vertex 2 from the reference unit cell, second one takes vertex 3.
2-element Vector{PeriodicGraphs.OffsetVertexIterator{2}}:
 [(2, (0,0)), (3, (-1,0))]
 [(2, (1,0)), (3, (0,0))]

julia> subgraph  # the subgraph consists in only the two relevant two vertices
PeriodicGraph2D(2, PeriodicEdge2D[(1, 2, (0,0)), (1, 2, (1,0))])

julia> mat  # the new cell is twice as large as the initial one
2×2 SMatrix{2, 2, Int64, 4} with indices SOneTo(2)×SOneTo(2):
 2  0
 0  1
```
