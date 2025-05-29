```
integer_lattice(S::Symbol, n::RationalUnion = 1) -> ZZlat
```

`S = :H` または `S = :U` の場合、主対角線に0、その他の要素に1を持つ2x2行列 $J_2$ を基底のいくつかでグラム行列として受け入れる $\mathbb Z$-格子を返します。
