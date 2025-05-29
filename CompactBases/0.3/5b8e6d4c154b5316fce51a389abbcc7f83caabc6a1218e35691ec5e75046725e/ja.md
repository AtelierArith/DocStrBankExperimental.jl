```
basis_overlap(A::FEDVROrRestricted, B)
```

FEDVRへの変換は有限差分とほぼ同じです。 quadratureノードで評価し、重みでスケールします。ただし、これは要素ごとに行う必要があるため、すでに設定されている補間ルーチンを通して処理します。
