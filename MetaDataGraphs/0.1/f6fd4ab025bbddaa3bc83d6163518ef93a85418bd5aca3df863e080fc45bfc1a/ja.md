```
AbstractDataGraph{T,VL,VD,ED,GD} <: AbstractGraph{T}
```

メタデータを持つグラフの一般的なテンプレート。

  * `T<:Integer` は頂点の型です
  * `VL` は頂点ラベルの型（`Integer` のサブタイプではない）
  * `VD` は頂点データオブジェクトの型です
  * `ED` はエッジデータオブジェクトの型です
  * `GD` はグラフデータオブジェクトの型です
