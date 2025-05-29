```
PointFluxes{GaugeT} <: AbstractField
```

与えられた点を通る小さな磁束のコレクションを表すオブジェクトです。フィールドはz軸に沿って指向しています。

## フィールド

  * `fluxes`: 磁束の値。
  * `points`: `NTuple{2,Float64}` の点のベクトル。
