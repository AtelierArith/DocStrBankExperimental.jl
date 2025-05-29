```
combine(A::AbstracRasterSeries; [dims], [lazy]) => Raster
```

Combine a `RasterSeries` along some dimension/s, creating a new `Raster` or `RasterStack`, depending on the contents of the series.

If `dims` are passed, only the specified dimensions will be combined with a `RasterSeries` returned, unless `dims` is all the dims in the series.

If `lazy`, concatenate lazily. The default is to concatenate lazily for lazy `Raster`s and eagerly otherwise.

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
