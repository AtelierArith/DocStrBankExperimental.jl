```
mutable struct RasterStackHistogram <: AbstractRasterHistogram
```

A `RasterStackHistogram`. The `struct` is `mutable` so that the `histogram` field can be updated using the `normalize` (or otherwise) function.

  * `layers::Any`: The layers (variables) from the `RasterStack` used to fit the `Histogram`
  * `dimensions::Any`: The dimensions of the `RasterStack`
  * `raster_size::Any`: The size of the `RasterStack` layers
  * `histogram::StatsBase.Histogram`: The N-dimensional `Histogram` fitted to the N layers from `RasterStack`
