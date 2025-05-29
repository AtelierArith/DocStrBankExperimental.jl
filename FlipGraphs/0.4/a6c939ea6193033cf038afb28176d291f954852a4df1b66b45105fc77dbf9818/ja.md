```
mcKay_edges(D::DeltaComplex; kwargs..) :: Vector{Vector{Int32}}
```

マッケイの標準グラフラベリングアルゴリズムを適用して、標準同型類の代表を与える `DualEdge` のすべての可能な置換を決定します。

`DualEdge` 1 が `DualEdge` `p[1]` になり、`DualEdge` 2 が `DualEdge` `p[2]` になるような置換ベクトル `p` のベクトルを返します。

# 引数

  * `only_one :: Bool = false`、true に設定すると、アルゴリズムは有効な置換を1つ見つけた後に停止します。
