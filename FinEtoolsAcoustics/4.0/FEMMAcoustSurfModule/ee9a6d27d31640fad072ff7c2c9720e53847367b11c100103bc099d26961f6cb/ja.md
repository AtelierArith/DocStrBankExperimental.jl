```
acousticcouplingpanels(self::FEMMAcoustSurf, geom::NodalField, u::NodalField{T}) where {T}
```

音響圧力-構造結合行列を計算します。

音響圧力-ノード力行列は、表面に分布する圧力を有限要素モデルのノードに作用する力に変換します。その転置は、変位（または速度、または加速度）を表面に沿った変位（または速度、または加速度）の法線成分に変換します。

# 引数

  * `geom`=幾何学フィールド
  * `u` = 変位フィールド

!!! 注

  * `n` = 外法線（音響媒体に向かって指す）。
  * 表面に沿った圧力は、各有限要素（パネル）に沿って一定（均一）であると仮定されます。パネル圧力は、セット内の有限要素のシリアル番号と同じ数値が与えられると仮定されます。
