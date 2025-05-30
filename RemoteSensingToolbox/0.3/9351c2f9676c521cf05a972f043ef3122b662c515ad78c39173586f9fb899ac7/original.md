```
apply_masks(raster, masks...)
```

Similar to `Rasters.mask`, but with the following differences:

1. Removes non-missing mask values instead of missing values. This is useful when working with cloud or shadow masks.
2. Accepts multiple masks, which are applied in sequence.

# Parameters

  * `raster`: The `AbstractRaster` or `AbstractRasterStack` to be masked.
  * `masks`: One or more masks to apply to the given raster.
