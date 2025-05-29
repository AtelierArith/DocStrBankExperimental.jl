```
missingmask(obj::Raster; kw...)
missingmask(obj; [to, res, size])
missingmask(obj::RasterStack; alllayers=true, kw...)
```

Create a mask array of `missing` and `true` values, from another `Raster`. `AbstractRasterStack` or `AbstractRasterSeries` are also accepted-

For [`AbstractRaster`](@ref) the default `missingval` is `missingval(A)`, but others can be chosen manually.

The array returned from calling `missingmask` on a `AbstractRaster` is a [`Raster`](@ref) with the same size and fields as the original array.

# Arguments

  * `obj`: a [`Raster`](@ref) or one or multiple geometries. Geometries can be   a GeoInterface.jl `AbstractGeometry`, a nested `Vector` of `AbstractGeometry`,   or a Tables.jl compatible object containing a `:geometry` column or points and values columns,   in which case `geometrycolumn` must be specified.

# Keywords

  * `alllayers`: if `true` a mask is taken for all layers, otherwise only the first layer is used. Defaults to `true`
  * `invert`: invert the mask, so that areas no missing in `with` are   masked, and areas missing in `with` are masked.
  * `to`: a `Raster`, `RasterStack`, `Tuple` of `Dimension` or `Extents.Extent`.   If no `to` object is provided the extent will be calculated from the geometries,   Additionally, when no `to` object or an `Extent` is passed for `to`, the `size`   or `res` keyword must also be used.
  * `res`: the resolution of the dimensions (often in meters or degrees), a `Real` or `Tuple{<:Real,<:Real}`.   Only required when `to` is not used or is an `Extents.Extent`, and `size` is not used.
  * `size`: the size of the output array, as a `Tuple{Int,Int}` or single `Int` for a square.   Only required when `to` is not used or is an `Extents.Extent`, and `res` is not used.
  * `crs`: a `crs` which will be attached to the resulting raster when `to` not passed  or is an `Extent`. Otherwise the crs from `to` is used.
  * `boundary`: for polygons, include pixels where the `:center` is inside the polygon,   where the polygon `:touches` the pixel, or that are completely `:inside` the polygon.   The default is `:center`.
  * `shape`: Force `data` to be treated as `:polygon`, `:line` or `:point` geometries.   using points or lines as polygons may have unexpected results.

  * `geometrycolumn`: `Symbol` to manually select the column the geometries are in   when `data` is a Tables.jl compatible table, or a tuple of `Symbol` for columns of   point coordinates.

# Example

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, Plots, Dates
wc = Raster(WorldClim{Climate}, :prec; month=1)
missingmask(wc) |> plot

savefig("build/missingmask_example.png"); nothing

# output
```

![missingmask](missingmask_example.png)

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
