```
mosaic!(f, dest::Union{Raster,RasterStack}, regions...; kw...)
mosaic!(f, dest::Union{Raster,RasterStack}, regions; kw...)
```

Combine `regions` of `Raster` or `RasterStack` into `dest` using the function `f` to combine overlapping areas.

# Arguments

  * `f`: A reducing function for values where `regions` overlap.    Note that common base functions    (`mean`, `sum`, `prod`, `first`, `last`, `minimum`, `maximum`,  `length`)   are optimised and will work on many memory or disk based files,   but user-defined functions may fail at larger scales unless `op` is passes as a keyword.
  * `regions`: Iterable of `Raster` or `RasterStack`. Using an `AbstractArray` is    usually better than a `Tuple` or splat when there are many regions.

  * `dest`: A `Raster` or `RasterStack`. May be a an opened disk-based `Raster`,   the result will be written to disk.   With the current algorithm, the read speed is slow.

# Keywords

  * `missingval`: Fills empty areas, and defaults to the   `missingval` of the first region.
  * `op`: an operator for the reduction, e.g. `add_sum` for `sum`.    For common methods like `sum` these are known and detected for you,    but you can provide it manually for other functions, so they continue   to work at large scales.
  * `atol`: Absolute tolerance for comparison between index values.   This is often required due to minor differences in range values   due to floating point error. It is not applied to non-float dimensions.   A tuple of tolerances may be passed, matching the dimension order.
  * `progress`: show a progress bar, `true` by default, `false` to hide.
  * `read`: `read` lazy raster regions before writing them. This may help   if there are chunk alignment issues between the source and dest rasters.   `false` by default.

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
