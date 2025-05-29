```
mutable struct RasterSeriesHistogram <: AbstractRasterHistogram
```

`RasterSeriesHistogram`は、`RasterSeries`の`child`が`RasterStack`または`Raster`である構造体です。この`struct`は`mutable`であるため、`histogram`フィールドは`normalize`（またはその他の）関数を使用して更新できます。

  * `layers::Any`: `Histogram`をフィットさせるために使用される`RasterSeries`のレイヤー（変数）
  * `series_dimension::Any`: `RasterSeries`の次元（通常、これは時間になります）
  * `series_length::Any`: `RasterSeries`の長さ
  * `dimensions::Any`: `RasterSeries`の要素（`Raster`または`RasterStack`のいずれか）の次元
  * `raster_size::Any`: `RasterSeries`の要素（`Raster`または`RasterStack`のいずれか）のサイズ
  * `histogram::StatsBase.Histogram`: `RasterSeries`のNレイヤーにフィットしたN次元の`Histogram`
