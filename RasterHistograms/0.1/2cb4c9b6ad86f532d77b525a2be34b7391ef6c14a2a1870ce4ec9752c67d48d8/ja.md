```
mutable struct RasterLayerHistogram <: AbstractRasterHistogram
```

`RasterLayerHistogram`。`struct`は`mutable`であるため、`histogram`フィールドは`normalize`（またはその他の）関数を使用して更新できます。

  * `layer::Any`: `Raster`からのレイヤー（変数）
  * `dimensions::Any`: `Raster`の次元
  * `raster_size::Any`: `Raster`のサイズ
  * `histogram::StatsBase.Histogram`: `Raster`レイヤーデータにフィットした1次元ヒストグラム
