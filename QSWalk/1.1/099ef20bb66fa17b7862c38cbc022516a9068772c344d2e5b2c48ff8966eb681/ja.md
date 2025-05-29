```
nm_init(init_states, vertexset)
```

`Dict{Vertex, <:AbstractMatrix{<:Number}}` 型の `init_states` に基づいて非道徳化進化の場合の初期状態を作成します。与えられた各頂点に対して辞書からブロックが使用され、それ以外の場合はゼロ行列が選択されます。辞書の各行列は非負であり、すべてのトレースの合計は1に等しくする必要があります。`init_vertices` のキーは `vertexset` の頂点である必要があります。頂点 `v` に対応する `init_states` の行列は `length(v)`×`length(v)` のサイズである必要があります。

*注意:* この関数は `ComplexF64` フィールド型の疎行列を返します。

# 例

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
