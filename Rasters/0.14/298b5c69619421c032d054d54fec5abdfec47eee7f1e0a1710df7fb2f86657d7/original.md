```
warp(A::AbstractRaster, flags::Dict; kw...)
```

Gives access to the GDALs `gdalwarp` method given a `Dict` of `flag => value` arguments that can be converted to strings, or vectors where multiple space-separated arguments are required.

Arrays with additional dimensions not handled by GDAL (other than `X`, `Y`, `Band`) are sliced, warped, and then combined to match the original array dimensions. These slices will *not* be written to disk and loaded lazily at this stage - you will need to do that manually if required.

See [the gdalwarp docs](https://gdal.org/programs/gdalwarp.html) for a list of arguments.

Run `using ArchGDAL` to make this method available.

# Keywords

  * `missingval`: value representing missing data, normally detected from the file and    automatically converted to `missing`. Setting to an alternate value, such as `0`    or `NaN` may be desirable for improved perfomance. `nothing` specifies no missing value.    Using the same `missingval` the file already has removes the overhead of replacing it,   this can be done by passing the `missingval` function as `missingval`.    If the file has an incorrect value, we can manually define the transformation   as a pair like `correct_value => missing` or `correct_value => NaN`.   `correct_value => correct_value` will keep remove the overhead of changing it.    Note: When `raw=true` is set, `missingval` is not changed from the value specified   in the file.
  * `filename`: a filename to write to directly, useful for large files.
  * `suffix`: a string or value to append to the filename.   A tuple of `suffix` will be applied to stack layers. `keys(stack)` are the default.
  * `missingval`: the missing value to use during warping, will default to   `Rasters.missingval(A). Passing a pair will specify the missing value    to use after warping.

Any additional keywords are passed to `ArchGDAL.Dataset`.

## Example

This simply resamples the array with the `:tr` (output file resolution) and `:r` flags, giving us a pixelated version:

```jldoctest
using Rasters, ArchGDAL, RasterDataSources, Plots
A = Raster(WorldClim{Climate}, :prec; month=1)
a = plot(A)

flags = Dict(
    :tr => [2.0, 2.0],
    :r => :near,
)
b = plot(warp(A, flags))

savefig(a, "build/warp_example_before.png");
savefig(b, "build/warp_example_after.png"); nothing

# output

```

### Before `warp`:

![before warp](warp_example_before.png)

### After `warp`:

![after warp](warp_example_after.png)

In practise, prefer [`resample`](@ref) for this. But `warp` may be more flexible.

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
