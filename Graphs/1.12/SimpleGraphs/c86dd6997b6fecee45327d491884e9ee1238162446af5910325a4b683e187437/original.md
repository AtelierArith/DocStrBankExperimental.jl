```
SimpleGraph{T}(adjm::AbstractMatrix)
```

Construct a `SimpleGraph{T}` from the adjacency matrix `adjm`. If `adjm[i][j] != 0`, an edge `(i, j)` is inserted. `adjm` must be a square and symmetric matrix. The element type `T` can be omitted.

## Examples

```jldoctest
julia> using Graphs

julia> A1 = [false true; true false];

julia> SimpleGraph(A1)
{2, 1} undirected simple Int64 graph

julia> A2 = [2 7; 7 0];

julia> SimpleGraph{Int16}(A2)
{2, 2} undirected simple Int16 graph
```
