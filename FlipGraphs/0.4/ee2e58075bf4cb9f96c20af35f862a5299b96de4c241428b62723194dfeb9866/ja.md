```
vertices(D::DeltaComplex, d::DualEdge) :: Tuple{TriFace, TriFace}
```

双辺 `d` に隣接する両方の頂点（`TriFace`）を返します。

最初の `TriFace` は辺の左側にあり、2番目のものは辺の右側にあります。
