```
slice(A::Union{AbstractRaster,AbstractRasterStack,AbstracRasterSeries}, dims) => RasterSeries
```

Slice views along some dimension/s to obtain a `RasterSeries` of the slices.

For a `Raster` or `RasterStack` this will return a `RasterSeries` of `Raster` or `RasterStack` that are slices along the specified dimensions.

For a `RasterSeries`, the output is another series where the child objects are sliced and the series dimensions index is now of the child dimensions combined. `slice` on a `RasterSeries` with no dimensions will slice along the dimensions shared by both the series and child object.

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
