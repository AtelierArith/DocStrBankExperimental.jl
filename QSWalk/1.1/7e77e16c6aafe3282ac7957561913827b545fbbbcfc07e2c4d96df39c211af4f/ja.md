```
nm_loc_ham(vertexset[, hamiltoniansByVertex])
```

`vertexset` の線形部分空間の各頂点に局所的に作用するハミルトニアンを返します。`hamiltoniansByVertex` は辞書 `Dict{Vertex, SparseDenseMatrix}` であり、特定の頂点に対して、その頂点の部分空間の次元と同じサイズのエルミート演算子を生成します。

*注:* `vertexset` の値は、非道徳化手続きを一致させるために `make_vertex_set` によって生成される必要があります。数値解析は、ハミルトニアンが複素数値であるべきであることを示唆しています。

# 例

```jldoctest; setup = :(using QSWalk)
julia> vset = VertexSet([[1, 2], [3, 4]])
VertexSet(Vertex[Vertex([1, 2]), Vertex([3, 4])])

julia> Matrix(nm_loc_ham(vset))
4×4 Array{Complex{Float64},2}:
 0.0+0.0im  0.0+1.0im  0.0+0.0im  0.0+0.0im
 0.0-1.0im  0.0+0.0im  0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im  0.0+0.0im  0.0+1.0im
 0.0+0.0im  0.0+0.0im  0.0-1.0im  0.0+0.0im

julia> A, B = [1 1im; -1im 1], [0 1; 1 0]
(Complex{Int64}[1 + 0im 0 + 1im; 0 - 1im 1 + 0im], [0 1; 1 0])

julia> v1, v2 = vlist(vset)
2-element Array{Vertex,1}:
 Vertex([1, 2])
 Vertex([3, 4])

julia> nm_loc_ham(vset, Dict{Vertex,Matrix{Number}}(v1  => A, v2  => B))
4×4 SparseArrays.SparseMatrixCSC{Complex{Float64},Int64} with 6 stored entries:
  [1, 1]  =  1.0+0.0im
  [2, 1]  =  0.0-1.0im
  [1, 2]  =  0.0+1.0im
  [2, 2]  =  1.0+0.0im
  [4, 3]  =  1.0+0.0im
  [3, 4]  =  1.0+0.0im
```
