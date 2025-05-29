```
mcKay_vertices(D::DeltaComplex; kwargs..) :: Vector{Vector{Int32}}
```

マッケイの標準グラフラベリングアルゴリズムのバージョンを適用して、標準同型類の代表を与えるすべての可能な `TriFace` の順列を決定します。

`TriFace` 1 が `TriFace` `p[1]` になり、`TriFace` 2 が `TriFace` `p[2]` になるような順列ベクトル `p` のベクトルを返します。 `only_one=true` の場合、アルゴリズムは有効な順列を1つ見つけた後に停止します。

# 引数

  * `only_one :: Bool = false`、true に設定すると、アルゴリズムは有効な順列を1つ見つけた後に停止します。
  * `A_deltacomplex :: Matrix{<:Integer} = Matrix{Int32}(adjacency*matrix*deltacomplex(D))`。提供された場合、アルゴリズムは `DeltaComplex` `D` の隣接行列を使用します。提供されない場合、アルゴリズムは自分で計算する必要があります。
