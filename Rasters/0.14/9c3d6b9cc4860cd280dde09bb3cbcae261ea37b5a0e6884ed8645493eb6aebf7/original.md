```
resample(x; kw...)
resample(xs...; to=first(xs), kw...)
```

`resample` uses `warp` (which uses GDALs `gdalwarp`) to resample a [`Raster`](@ref) or [`RasterStack`](@ref) to a new `resolution` and optionally new `crs`, or to snap to the bounds, resolution and crs of the object `to`.

Dimensions without an `AbstractProjected` lookup (such as a `Ti` dimension) are iteratively resampled with GDAL and joined back into a single array.

If projections can be converted for each axis independently, it may be faster and more accurate to use [`reproject`](@ref).

Run `using ArchGDAL` to make this method available.

# Arguments

  * `x`: the object/s to resample.

# Keywords

  * `to`: a `Raster`, `RasterStack`, `Tuple` of `Dimension` or `Extents.Extent`.   If no `to` object is provided the extent will be calculated from `x`,
  * `res`: the resolution of the dimensions (often in meters or degrees), a `Real` or `Tuple{<:Real,<:Real}`.   Only required when `to` is not used or is an `Extents.Extent`, and `size` is not used.
  * `size`: the size of the output array, as a `Tuple{Int,Int}` or single `Int` for a square.   Only required when `to` is not used or is an `Extents.Extent`, and `res` is not used.
  * `crs`: a `crs` which will be attached to the resulting raster when `to` not passed  or is an `Extent`. Otherwise the crs from `to` is used.
  * `method`: A `Symbol` or `String` specifying the method to use for resampling.   From the docs for [`gdalwarp`](https://gdal.org/programs/gdalwarp.html#cmdoption-gdalwarp-r):

      * `:near`: nearest neighbour resampling (default, fastest algorithm, worst interpolation quality).
      * `:bilinear`: bilinear resampling.
      * `:cubic`: cubic resampling.
      * `:cubicspline`: cubic spline resampling.
      * `:lanczos`: Lanczos windowed sinc resampling.
      * `:average`: average resampling, computes the weighted average of all non-NODATA contributing pixels.   rms root mean square / quadratic mean of all non-NODATA contributing pixels (GDAL >= 3.3)
      * `:mode`: mode resampling, selects the value which appears most often of all the sampled points.
      * `:max`: maximum resampling, selects the maximum value from all non-NODATA contributing pixels.
      * `:min`: minimum resampling, selects the minimum value from all non-NODATA contributing pixels.
      * `:med`: median resampling, selects the median value of all non-NODATA contributing pixels.
      * `:q1`: first quartile resampling, selects the first quartile value of all non-NODATA contributing pixels.
      * `:q3`: third quartile resampling, selects the third quartile value of all non-NODATA contributing pixels.
      * `:sum`: compute the weighted sum of all non-NODATA contributing pixels (since GDAL 3.1)

    Where NODATA values are set to `missingval`.
  * `filename`: a filename to write to directly, useful for large files.
  * `suffix`: a string or value to append to the filename.   A tuple of `suffix` will be applied to stack layers. `keys(stack)` are the default.

Note:

  * GDAL may cause some unexpected changes in the raster, such as changing the `crs`   type from `EPSG` to `WellKnownText` (it will represent the same CRS).

# Example

Resample a WorldClim layer to match an EarthEnv layer:

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, Plots
A = Raster(WorldClim{Climate}, :prec; month=1)
B = Raster(EarthEnv{HabitatHeterogeneity}, :evenness)

a = plot(A)
b = plot(resample(A; to=B))

savefig(a, "build/resample_example_before.png");
savefig(b, "build/resample_example_after.png"); nothing

# output
```

### Before `resample`:

![before resample](resample_example_before.png)

### After `resample`:

![after resample](resample_example_after.png)

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
