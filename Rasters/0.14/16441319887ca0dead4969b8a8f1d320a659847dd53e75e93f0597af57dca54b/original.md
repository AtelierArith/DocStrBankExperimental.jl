```
mask(A:AbstractRaster; with, missingval=missingval(A))
mask(x; with)
```

Return a new array with values of `A` masked by the missing values of `with`, or by the shape of `with`, if `with` is a geometric object.

# Arguments

  * `x`: a `Raster` or `RasterStack`

# Keywords

  * `with`: an `AbstractRaster`, or any GeoInterface.jl compatible objects   or table. The coordinate reference system of the point must match `crs(A)`.
  * `invert`: invert the mask, so that areas no missing in `with` are   masked, and areas missing in `with` are masked.
  * `missingval`: the missing value to use in the returned file.
  * `filename`: a filename to write to directly, useful for large files.
  * `suffix`: a string or value to append to the filename.   A tuple of `suffix` will be applied to stack layers. `keys(stack)` are the default.

# Geometry keywords

These can be used when `with` is a GeoInterface.jl compatible object:

  * `shape`: Force `data` to be treated as `:polygon`, `:line` or `:point` geometries.   using points or lines as polygons may have unexpected results.
  * `boundary`: for polygons, include pixels where the `:center` is inside the polygon,   where the polygon `:touches` the pixel, or that are completely `:inside` the polygon.   The default is `:center`.
  * `geometrycolumn`: `Symbol` to manually select the column the geometries are in   when `data` is a Tables.jl compatible table, or a tuple of `Symbol` for columns of   point coordinates.

# Example

Mask an unmasked AWAP layer with a masked WorldClim layer, by first resampling the mask.

```julia
using Rasters, RasterDataSources, ArchGDAL, Plots, Dates

# Load and plot the file
awap = read(Raster(AWAP, :tmax; date=DateTime(2001, 1, 1)))
a = plot(awap; clims=(10, 45))

# Create a mask my resampling a worldclim file
wc = Raster(WorldClim{Climate}, :prec; month=1)
wc_mask = resample(wc; to=awap)

# Mask
awap_masked = mask(awap; with=wc_mask)
b = plot(awap_masked; clims=(10, 45))

savefig(a, "build/mask_example_before.png");
savefig(b, "build/mask_example_after.png"); nothing
# output

```

### Before `mask`:

### After `mask`:

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
