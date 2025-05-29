```
nm_loc_ham(vertexset[, hamiltoniansByDegree])
```

`vertexset` の線形部分空間の各頂点に局所的に作用するハミルトニアンを返します。`hamiltoniansByDegree` は辞書 `Dict{Int, SparseDenseMatrix}` であり、与えられた頂点の線形部分空間の次元に対してエルミート演算子を生成します。既存の次元に対してのみ行列を指定する必要があります。

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

julia> A = [1 1im; -1im 1]
2×2 Array{Complex{Int64},2}:
 1+0im  0+1im
 0-1im  1+0im

julia> nm_loc_ham(vset, Dict{Int,Matrix{ComplexF64}}(2  => A))
4×4 SparseArrays.SparseMatrixCSC{Complex{Float64},Int64} with 8 stored entries:
  [1, 1]  =  1.0+0.0im
  [2, 1]  =  0.0-1.0im
  [1, 2]  =  0.0+1.0im
  [2, 2]  =  1.0+0.0im
  [3, 3]  =  1.0+0.0im
  [4, 3]  =  0.0-1.0im
  [3, 4]  =  0.0+1.0im
  [4, 4]  =  1.0+0.0im
```
