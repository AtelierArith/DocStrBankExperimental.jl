```
nm_init(init_vertices, vertexset)
```

`Vector{Vertex}`型の`init_vertices`に基づいて、非道徳化進化の場合の初期状態を作成します。結果はブロック対角行列であり、各ブロックは`vertexset`の頂点に対応します。最終状態は`nm_measurement`に対する一様確率を表します。

*注:* この関数は`ComplexF64`フィールド型の疎行列を返します。

# 例

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
