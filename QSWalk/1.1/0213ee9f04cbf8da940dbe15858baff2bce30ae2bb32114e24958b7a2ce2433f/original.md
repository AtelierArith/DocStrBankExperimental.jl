```
nm_glob_ham(A[, hamiltonians][, weights, epsilon])
```

Return global Hamiltonian for the moralization procedure. Matrix `A` should the adjacency matrix of a directed graph, for which one aims to construct the nonmoralizing dynamics. Here, `hamiltonians` is an optional argument which is a Dictionary with keys of type `Tuple{Int, Int}` or `Tuple{Vertex, Vertex}`. The first collects the submatrices according to their shape, while the second collects them according to each pair of vertices. As the default all-one submatrices are chosen. The last argument states that only those elements for which `abs(A[i, j]) >= epsilon` are considered.

*Note:* The submatrices of the result matrix are scaled by corresponding `weights` argument, which should be a square matrix of the same dimension as `A`. If `weights` is not provided, then `weights[i,j]=A[i,j]`, if `A[i,j]` is nonzero and `A[j,i]` is zero, `weights[i,j]=A[j,i]`, if `A[i,j]` in reverse scenario, `weights[i,j]=(A[i,j]+A[j,i])/2` if both are nonzero, and zero otherwise.

# Examples

```jldoctest; setup = :(using QSWalk)
julia> A = [ 0 1 0; 1 0 1; 0 1 0]
3×3 Array{Int64,2}:
 0  1  0
 1  0  1
 0  1  0

julia> nm_glob_ham(A) |> Matrix
4×4 Array{Complex{Float64},2}:
 0.0+0.0im  1.0+0.0im  1.0+0.0im  0.0+0.0im
 1.0+0.0im  0.0+0.0im  0.0+0.0im  1.0+0.0im
 1.0+0.0im  0.0+0.0im  0.0+0.0im  1.0+0.0im
 0.0+0.0im  1.0+0.0im  1.0+0.0im  0.0+0.0im

julia> dict_deg = Dict{Tuple{Int,Int},Matrix{ComplexF64}}((1, 2) => (2+1im)*ones(1, 2), (2, 1) =>1im*ones(2, 1));

julia> nm_glob_ham(A, dict_deg) |> Matrix
4×4 Array{Complex{Float64},2}:
 0.0+0.0im  2.0+1.0im  2.0+1.0im  0.0+0.0im
 2.0-1.0im  0.0+0.0im  0.0+0.0im  0.0+1.0im
 2.0-1.0im  0.0+0.0im  0.0+0.0im  0.0+1.0im
 0.0+0.0im  0.0-1.0im  0.0-1.0im  0.0+0.0im

julia> v1, v2, v3 = vlist(make_vertex_set(A))
3-element Array{Vertex,1}:
 Vertex([1])
 Vertex([2, 3])
 Vertex([4])

julia> dict_vec = Dict{Tuple{Vertex,Vertex},Matrix{ComplexF64}}((v1, v2) =>2*ones(1, 2), (v2, v3) =>[1im 2im;]');

julia> nm_glob_ham(A, dict_vec) |> Matrix
4×4 Array{Complex{Float64},2}:
 0.0+0.0im  2.0+0.0im  2.0+0.0im  0.0+0.0im
 2.0+0.0im  0.0+0.0im  0.0+0.0im  0.0-1.0im
 2.0+0.0im  0.0+0.0im  0.0+0.0im  0.0-2.0im
 0.0+0.0im  0.0+1.0im  0.0+2.0im  0.0+0.0im
```
