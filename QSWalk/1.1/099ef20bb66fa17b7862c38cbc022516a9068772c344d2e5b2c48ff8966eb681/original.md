```
nm_init(init_states, vertexset)
```

Create initial state in the case of the nonmoralizing evolution based on `init_states` of type `Dict{Vertex, <:AbstractMatrix{<:Number}}`. For each given vertex a block from dictionary is used, otherwise zero matrix is chosen. Each matrix from dictionary should be nonnegative and sum of all traces should equal one. The keys of `init_vertices` should be a vertices from `vertexset`. Note that matrix from `init_states` corresponding to vertex `v` should be of size `length(v)`×`length(v)`.

*Note:* The function returns sparse matrix with `ComplexF64` field type.

# Examples

```jldoctest; setup = :(using QSWalk)
julia> vset = VertexSet([[1], [2, 3, 4], [5, 6, 7], [8, 9]])
VertexSet(Vertex[Vertex([1]), Vertex([2, 3, 4]), Vertex([5, 6, 7]), Vertex([8, 9])])

julia> A1, A2, A3 = ones(ComplexF64, 1, 1)/4, [ 1/5+0im 0 1/5; 0 1/10 0 ; 1/5 0 1/5 ], [0.125 -0.125+0im; -0.125 0.125]
(Complex{Float64}[0.25 + 0.0im], Complex{Float64}[0.2 + 0.0im 0.0 + 0.0im 0.2 + 0.0im; 0.0 + 0.0im 0.1 + 0.0im 0.0 + 0.0im; 0.2 + 0.0im 0.0 + 0.0im 0.2 + 0.0im], Complex{Float64}[0.125 + 0.0im -0.125 + 0.0im; -0.125 + 0.0im 0.125 + 0.0im])

julia> nm_init(Dict(vset[1] =>A1, vset[3] =>A2, vset[4] =>A3), vset)
9×9 SparseArrays.SparseMatrixCSC{Complex{Float64},Int64} with 10 stored entries:
  [1, 1]  =  0.25+0.0im
  [5, 5]  =  0.2+0.0im
  [7, 5]  =  0.2+0.0im
  [6, 6]  =  0.1+0.0im
  [5, 7]  =  0.2+0.0im
  [7, 7]  =  0.2+0.0im
  [8, 8]  =  0.125+0.0im
  [9, 8]  =  -0.125+0.0im
  [8, 9]  =  -0.125+0.0im
  [9, 9]  =  0.125+0.0im

```
