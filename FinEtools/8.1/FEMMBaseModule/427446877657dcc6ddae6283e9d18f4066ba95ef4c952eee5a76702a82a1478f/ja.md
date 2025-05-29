```
dualconnectionmatrix(
    self::FEMM,
    fens::FENodeSet,
    minnodes = 1,
) where {FEMM<:AbstractFEMM}
```

双接続行列を計算します。

この行列は、いくつかの有限要素ノードによって接続されている要素に対応するすべての行と列に非ゼロの値を持ちます。

  * `minnodes`: 要素が隣接するために共有する必要がある最小ノード数（デフォルトは1）
