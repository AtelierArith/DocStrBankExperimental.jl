```
AdjacencyMatrix(g::AbstractGraph)
```

A matrix view of a graph.

Entry `(i, j)` is `true` if `i -> j` is and edge of `g` and `false` otherwise.

As this is as a view, the entries and the size of this matrix can change when the underlying graph changes. The view itself is immutable. Convert to a `Matrix` or `SparseMatrixCSC` to get a mutable matrix that does not change when the graph does.

### See also

[`adjacency_matrix`](@ref), [`ValMatrix`](@ref), [`weigths`](@ref)

### Examples

```jldoctest
julia> g = complete_bipartite_graph(2, 2)
{4, 4} undirected simple Int64 graph

julia> AdjacencyMatrix(g)
4×4 AdjacencyMatrix{SimpleGraph{Int64}}:
 0  0  1  1
 0  0  1  1
 1  1  0  0
 1  1  0  0

julia> AdjacencyMatrix(g) |> Matrix
4×4 Matrix{Bool}:
 0  0  1  1
 0  0  1  1
 1  1  0  0
 1  1  0  0
```
