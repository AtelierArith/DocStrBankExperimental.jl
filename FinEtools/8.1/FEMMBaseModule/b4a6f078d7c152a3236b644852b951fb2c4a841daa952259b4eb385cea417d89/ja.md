```
connectionmatrix(self::FEMM, nnodes) where {FEMM<:AbstractFEMM}
```

接続行列を計算します。

この行列は、いくつかの有限要素によって接続されているノードに対応するすべての行と列に非ゼロの値を持ちます。
