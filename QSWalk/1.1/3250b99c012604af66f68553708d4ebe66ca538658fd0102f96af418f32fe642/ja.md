```
nm_lind(A[, lindbladians][, epsilon])
```

単一のリンブラディアン演算子と、頂点がサブスペースにどのように結びついているかを示す頂点セットを返します。この演算子は、[1]で提示された補正スキームに従って構築されます。パラメータ`A`は正方行列で、隣接行列と同様に、標準サブスペース間の接続を記述します。パラメータ`epsilon`はデフォルト値`eps()`を持ち、`abs(A[i, j]) >=  epsilon`の式によって関連する値を決定します。リスト`lindbladians`は使用される基本行列を記述します。これは`Dict{Int, SparseDenseMatrix}`であり、入次数によって行列を返すか、`Dict{Vertex, SparseDenseMatrix}`であり、異なる頂点に対して異なる行列を返すことができます。行列は直交列を持ち、頂点の出次数のサイズである必要があります。デフォルトでは、関数はフーリエ行列を使用します。

*注:* すべての頂点のペアに対して、`lindbladians`リストに行列が存在することが期待されます。

*注:* `lindbladians`内の行列の直交性は検証されていません。

*注:* 結果行列の部分行列は、対応する`A`要素によって乗算されます。

[1] K. Domino, A. Glos, M. Ostaszewski, Superdiffusive quantum stochastic walk definable on arbitrary directed graph, Quantum Information & Computation, Vol.17 No.11&12, pp. 0973-0986, arXiv:1701.04624.

# 例

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
