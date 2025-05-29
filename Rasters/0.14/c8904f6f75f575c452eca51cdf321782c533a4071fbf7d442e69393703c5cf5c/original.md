```
replace_missing(a::AbstractRaster, newmissingval)
replace_missing(a::AbstractRasterStack, newmissingval)
```

Replace missing values in the array or stack with a new missing value, also updating the `missingval` field/s.

# Keywords

  * `filename`: a filename to write to directly, useful for large files.
  * `suffix`: a string or value to append to the filename.   A tuple of `suffix` will be applied to stack layers. `keys(stack)` are the default.

# Example

```jldoctest
using Rasters, RasterDataSources, ArchGDAL
A = Raster(WorldClim{Climate}, :prec; month=1) |> replace_missing
missingval(A)
# output
missing
```
