```
mcKay(g::TriangulatedPolygon) :: Vector{Vector{<:Integer}}
```

*マッケイの標準グラフラベリングアルゴリズム*を適用して、標準同型類の代表を与える頂点のすべての可能な順列を決定します。

i 番目の点が `p[i]` 番目の点としてラベル付けされるすべての可能な標準点ラベリング順列 `p` のリストを返します。
