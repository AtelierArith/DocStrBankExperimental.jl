```
mutable struct RasterSeriesHistogram <: AbstractRasterHistogram
```

A `RasterSeriesHistogram` where the `child`s of the `RasterSeries` are `RasterStack`s or `Raster`s. The `struct` is `mutable` so that the `histogram` field can be updated using the `normalize` (or otherwise) function.

  * `layers::Any`: The layers (variables) from the `RasterSeries` used to fit the `Histogram`
  * `series_dimension::Any`: The dimension of the `RasterSeries` (usually this will be time)
  * `series_length::Any`: The length of the `RasterSeries
  * `dimensions::Any`: The dimensions of the elements (either a `Raster` or `RasterStack`) of the `RasterSeries`
  * `raster_size::Any`: The size of the elements (either a `Raster` or `RasterStack`) of the `RasterSeries`
  * `histogram::StatsBase.Histogram`: The N-dimensional `Histogram` fitted to the N layers from `RasterSeries`
