```
mutable struct RasterStackHistogram <: AbstractRasterHistogram
```

`RasterStackHistogram`。`struct`は`mutable`であるため、`histogram`フィールドは`normalize`（またはその他の）関数を使用して更新できます。

  * `layers::Any`: `Histogram`をフィットさせるために使用される`RasterStack`からのレイヤー（変数）
  * `dimensions::Any`: `RasterStack`の次元
  * `raster_size::Any`: `RasterStack`レイヤーのサイズ
  * `histogram::StatsBase.Histogram`: `RasterStack`からのNレイヤーにフィットしたN次元の`Histogram`
