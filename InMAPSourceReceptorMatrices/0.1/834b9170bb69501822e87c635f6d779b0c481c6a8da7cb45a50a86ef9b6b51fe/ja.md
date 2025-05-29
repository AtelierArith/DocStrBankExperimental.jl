```
SparseSRM(emis_type, source_idxs, [layer_idxs]; threshold=0.0)
```

スパースソースレセプターマトリックスを作成し、(receptor, source, layer)でインデックス可能にします。

  * `emis_type` - スパースマトリックスを作成するための排出タイプ、∈ ("PrimaryPM25", "SOA", "pNO3", "pSO4", "pNH4")
  * `source_idxs` - マトリックスに汚染効果を追加するためのソースインデックスのベクトル
  * `layer_idxs` -
  * `threshold=0.0` - スパースマトリックスに値を追加するための閾値（単位 (μg / m³) / (μg / s)）。デフォルトでは、すべての非ゼロ値が追加されます。
