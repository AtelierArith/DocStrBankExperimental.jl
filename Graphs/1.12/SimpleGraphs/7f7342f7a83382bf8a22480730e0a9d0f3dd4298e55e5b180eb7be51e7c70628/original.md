```
SimpleDiGraph{T}(adjm::AbstractMatrix)
```

Construct a `SimpleDiGraph{T}` from the adjacency matrix `adjm`. If `adjm[i][j] != 0`, an edge `(i, j)` is inserted. `adjm` must be a square matrix. The element type `T` can be omitted.

## Examples

```jldoctest
julia> using Graphs

julia> A1 = [false true; false false]
2×2 Matrix{Bool}:
 0  1
 0  0

julia> SimpleDiGraph(A1)
{2, 1} directed simple Int64 graph

julia> A2 = [2 7; 5 0]
2×2 Matrix{Int64}:
 2  7
 5  0

julia> SimpleDiGraph{Int16}(A2)
{2, 3} directed simple Int16 graph
```
