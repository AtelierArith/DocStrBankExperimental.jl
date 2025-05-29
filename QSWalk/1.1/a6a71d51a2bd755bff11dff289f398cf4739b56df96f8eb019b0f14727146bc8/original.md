```
nm_init(init_vertices, vertexset)
```

Create initial state in the case of the nonmoralizing evolution based on `init_vertices` of type `Vector{Vertex}`. The result is a block diagonal matrix, where each block corresponds to vertex from `vertexset`. The final state represent an uniform probability over `nm_measurement`.

*Note:* The function returns sparse matrix with `ComplexF64` field type.

# Examples

```jldoctest; setup = :(using QSWalk)
julia> vset = VertexSet([[1], [2, 3, 4], [5, 6, 7], [8, 9]])
VertexSet(Vertex[Vertex([1]), Vertex([2, 3, 4]), Vertex([5, 6, 7]), Vertex([8, 9])])

julia> nm_init(vset[[1, 3, 4]], vset)
9×9 SparseArrays.SparseMatrixCSC{Complex{Float64},Int64} with 6 stored entries:
  [1, 1]  =  0.333333+0.0im
  [5, 5]  =  0.111111+0.0im
  [6, 6]  =  0.111111+0.0im
  [7, 7]  =  0.111111+0.0im
  [8, 8]  =  0.166667+0.0im
  [9, 9]  =  0.166667+0.0im
```
