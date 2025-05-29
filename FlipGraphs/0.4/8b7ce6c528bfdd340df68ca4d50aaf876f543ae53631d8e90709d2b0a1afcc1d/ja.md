```
mcKay_vertices(D::DeltaComplex; , A_deltacomplex::Matrix{<:Integer}, point_perm::Vector{<:Integer}) :: Vector{Vector{Int32}}
```

マッケイの標準グラフラベリングアルゴリズムのバージョンを適用して、標準同型類の代表を与えるすべての可能な `TriFace` の置換を決定します。

`TriFace` 1 が `TriFace` `p[1]` になり、`TriFace` 2 が `TriFace` `p[2]` になるような置換ベクトル `p` のベクトルを返します。 `only_one=true` の場合、アルゴリズムは有効な置換を1つ見つけた後に停止します。

ベクトル `point_perm` は、`D` の点が実際に変更されることなく、どのように名前が変更されたと見なされるかを決定します。
