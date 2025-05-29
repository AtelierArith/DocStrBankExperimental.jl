```
mutable struct RasterLayerHistogram <: AbstractRasterHistogram
```

A `RasterLayerHistogram`. The `struct` is `mutable` so that the `histogram` field can be updated using the `normalize` (or otherwise) function.

  * `layer::Any`: The layer (variable) from the `Raster`
  * `dimensions::Any`: The dimensions of the `Raster`
  * `raster_size::Any`: The size of the `Raster`
  * `histogram::StatsBase.Histogram`: The 1-dimensional histogram fitted to the `Raster` layer data
