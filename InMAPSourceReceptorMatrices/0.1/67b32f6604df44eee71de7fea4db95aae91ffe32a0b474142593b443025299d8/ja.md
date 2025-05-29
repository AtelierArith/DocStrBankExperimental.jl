```
SparseSRM(srm, source_idxs, [layer_idxs]; threshold=0.0)
```

SRM（`Array{Float32, 3}`）からスパースソースレセプターマトリックスを作成します。

  * `emis_type` - スパースマトリックスを作成するための排出タイプ。
  * `source_idxs` - マトリックスに汚染効果を追加するためのソースインデックスのベクトル
  * `layer_idxs` -
  * `threshold=0.0` - スパースマトリックスに値を追加するための閾値（μg / m³） / （μg / s）。デフォルトでは、すべての非ゼロ値が追加されます。
