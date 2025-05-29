```
PointFlux{GaugeT} <: AbstractField
```

与えられた点を通る小さな磁束を表すオブジェクトです。フィールドはz軸に沿って方向付けられています。

## フィールド

  * `flux`: 磁束の値。
  * `point`: 点のxおよびy座標の`Tuple`。
