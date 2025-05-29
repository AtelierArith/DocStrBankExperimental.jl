```
nm_lind(A[, lindbladians][, epsilon])
```

Return single Lindbladian operator and a vertex set describing how vertices are bound to subspaces. The operator is constructed according to the corection scheme presented in [1]. Parameter `A` is a square matrix, describing the connection between the canonical subspaces in a similar manner as the adjacency matrix. Parameter `epsilon`, with the default value `eps()`, determines the relevant values by `abs(A[i, j]) >=  epsilon` formula. List `lindbladians` describes the elementary matrices used. It can be `Dict{Int, SparseDenseMatrix}`, which returns the matrix by the indegree, or `Dict{Vertex, SparseDenseMatrix}` which, for different vertices, may return different matrix. The matrix should have orthogonal columns and be of the size outdeg of the vertex. As default the function uses Fourier matrices.

*Note:* It is expected that for all pair of vertices there exists a matrix in the `lindbladians` list.

*Note:* The orthogonality of matrices in `lindbladians` is not verified.

*Note:* The submatrices of the result matrix are multiplied by corresponding `A` element.

[1] K. Domino, A. Glos, M. Ostaszewski, Superdiffusive quantum stochastic walk definable on arbitrary directed graph, Quantum Information & Computation, Vol.17 No.11&12, pp. 0973-0986, arXiv:1701.04624.

# Examples

```jldoctest; setup = :(using QSWalk, LinearAlgebra)
julia> A = [0 1 0; 1 0 1; 0 1 0]
3×3 Array{Int64,2}:
 0  1  0
 1  0  1
 0  1  0

julia> L, vset = nm_lind(A)
(
  [2, 1]  =  1.0+0.0im
  [3, 1]  =  1.0+0.0im
  [1, 2]  =  1.0+0.0im
  [4, 2]  =  1.0+0.0im
  [1, 3]  =  1.0+0.0im
  [4, 3]  =  1.0+0.0im
  [2, 4]  =  1.0+0.0im
  [3, 4]  =  -1.0+1.22465e-16im, VertexSet(Vertex[Vertex([1]), Vertex([2, 3]), Vertex([4])]))

julia> B1, B2 = 2*diagm(0=>[1.]), 3*ones(2, 2)
([2.0], [3.0 3.0; 3.0 3.0])

julia> nm_lind(A, Dict{Int,Matrix{Float64}}(1=>B1, 2=>B2))
(
  [2, 1]  =  3.0+0.0im
  [3, 1]  =  3.0+0.0im
  [1, 2]  =  2.0+0.0im
  [4, 2]  =  2.0+0.0im
  [1, 3]  =  2.0+0.0im
  [4, 3]  =  2.0+0.0im
  [2, 4]  =  3.0+0.0im
  [3, 4]  =  3.0+0.0im, VertexSet(Vertex[Vertex([1]), Vertex([2, 3]), Vertex([4])]))

julia> v1, v2, v3 = vlist(vset)
3-element Array{Vertex,1}:
 Vertex([1])
 Vertex([2, 3])
 Vertex([4])

julia> nm_lind(A, Dict{Vertex,Matrix{Float64}}(v1 => ones(1, 1), v2 => [2 2; 2 -2], v3 => 3*ones(1, 1)))[1] |> Matrix
4×4 Array{Complex{Float64},2}:
 0.0+0.0im  1.0+0.0im  1.0+0.0im   0.0+0.0im
 2.0+0.0im  0.0+0.0im  0.0+0.0im   2.0+0.0im
 2.0+0.0im  0.0+0.0im  0.0+0.0im  -2.0+0.0im
 0.0+0.0im  3.0+0.0im  3.0+0.0im   0.0+0.0im
```
