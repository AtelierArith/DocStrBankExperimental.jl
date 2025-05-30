```
statistics(raster; stats=:all, fraction=1.0)
```

Calculate summary statistics for the provided `Raster` or `RasterStack`.

# Parameters

  * `raster`: An `AbstractRaster` or `AbstractRasterStack`.
  * `stats`: A `Vector` or `Tuple` containing any combination of the symbols :mean, :std, and :cov.
  * `fraction`: The fraction of pixels to sample when calculating statistics.

# Returns

A named tuple containing each requested statistic.
