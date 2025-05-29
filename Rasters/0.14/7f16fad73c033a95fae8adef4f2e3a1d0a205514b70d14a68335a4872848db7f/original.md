```
mask!(x; with, missingval=missingval(A))
```

Mask `A` by the missing values of `with`, or by all values outside `with` if it is a polygon.

If `with` is a polygon, creates a new array where points falling outside the polygon have been replaced by `missingval(A)`.

Return a new array with values of `A` masked by the missing values of `with`, or by a polygon.

# Arguments

  * `x`: a `Raster` or `RasterStack`.

# Keywords

  * `with`: another `AbstractRaster`, a `AbstractVector` of `Tuple` points,   or any GeoInterface.jl `AbstractGeometry`. The coordinate reference system   of the point must match `crs(A)`.
  * `invert`: invert the mask, so that areas no missing in `with` are   masked, and areas missing in `with` are masked.
  * `missingval`: the missing value to write to A in masked areas,   by default `missingval(A)`.

# Example

Mask an unmasked AWAP layer with a masked WorldClim layer, by first resampling the mask to match the size and projection.

```julia
using Rasters, RasterDataSources, ArchGDAL, Plots, Dates

# Load and plot the file
awap = read(RasterStack(AWAP, (:tmin, :tmax); date=DateTime(2001, 1, 1)))
a = plot(awap; clims=(10, 45), c=:imola)

# Create a mask my resampling a worldclim file
wc = Raster(WorldClim{Climate}, :prec; month=1)
wc_mask = resample(wc; to=awap)

# Mask
mask!(awap; with=wc_mask)
b = plot(awap; clims=(10, 45))

savefig(a, "build/mask_bang_example_before.png");
savefig(b, "build/mask_bang_example_after.png"); nothing

# output

```

### Before `mask!`:

### After `mask!`:

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
