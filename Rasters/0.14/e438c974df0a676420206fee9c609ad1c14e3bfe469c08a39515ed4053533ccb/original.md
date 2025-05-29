```
reproject(obj; crs)
```

Reproject the lookups of `obj` to a different crs. 

This is a lossless operation for the raster data, as only the  lookup values change. This is only possible when the axes of source and destination projections are aligned: the change is usually from a [`Regular`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Lookups.Regular) and an [`Irregular`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Lookups.Irregular) lookup spans.

For converting between projections that are rotated,  skewed or warped in any way, use [`resample`](@ref).

Dimensions without an `AbstractProjected` lookup (such as a `Ti` dimension) are silently returned without modification.

# Arguments

  * `obj`: a `Lookup`, `Dimension`, `Tuple` of `Dimension`, `Raster` or `RasterStack`.
  * `crs`: a `crs` which will be attached to the resulting raster when `to` not passed  or is an `Extent`. Otherwise the crs from `to` is used.
