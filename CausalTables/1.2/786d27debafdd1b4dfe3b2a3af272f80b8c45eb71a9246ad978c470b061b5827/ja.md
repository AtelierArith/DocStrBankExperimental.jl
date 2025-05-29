```
mutable struct Friends <: NetworkSummary
```

隣接行列における接続された個人の数をカウントするNetworkSummary、別名「友達」の数です。

# フィールド

  * `matrix::Symbol`: `StructuralCausalModel`の`DataGeneratingProcess`において要約が計算される隣接行列を示すキー；または、`CausalTable`の`arrays`属性における隣接行列のキー。
