```
rasterize!([reducer], dest, data; kw...)
```

Rasterize the geometries in `data` into the [`Raster`](@ref) or [`RasterStack`](@ref) `dest`, using the values specified by `fill`.

# Arguments

  * `dest`: a `Raster` or `RasterStack` to rasterize into.
  * `reducer`: a reducing function to reduce the fill value for all geometries that   cover or touch a pixel down to a single value. The default is `last`.   Any  that takes an iterable and returns a single value will work, including   custom functions. However, there are optimisations for built-in methods   including `sum`, `first`, `last`, `minimum`, `maximum`, `extrema` and `Statistics.mean`.   These may be an order of magnitude or more faster than   `count` is a special-cased as it does not need a fill value.
  * `data`: a GeoInterface.jl `AbstractGeometry`, a nested `Vector` of `AbstractGeometry`,   or a Tables.jl compatible object containing a `:geometry` column or points and values columns,   in which case `geometrycolumn` must be specified.

# Keywords

These are detected automatically from `A` and `data` where possible.

  * `fill`: the value or values to fill a polygon with. A `Symbol` or tuple of `Symbol` will   be used to retrieve properties from features or column values from table rows. An array   or other iterable will be used for each geometry, in order. `fill` can also be a function of    the current value, e.g. `x -> x + 1`.
  * `op`: A reducing function that accepts two values and returns one, like `min` to `minimum`.   For common methods this will be assigned for you, or is not required. But you can use it   instead of a `reducer` as it will usually be faster.
  * `to`: a `Raster`, `RasterStack`, `Tuple` of `Dimension` or `Extents.Extent`.   If no `to` object is provided the extent will be calculated from the geometries,   Additionally, when no `to` object or an `Extent` is passed for `to`, the `size`   or `res` keyword must also be used.
  * `res`: the resolution of the dimensions (often in meters or degrees), a `Real` or `Tuple{<:Real,<:Real}`.   Only required when `to` is not used or is an `Extents.Extent`, and `size` is not used.
  * `size`: the size of the output array, as a `Tuple{Int,Int}` or single `Int` for a square.   Only required when `to` is not used or is an `Extents.Extent`, and `res` is not used.
  * `crs`: a `crs` which will be attached to the resulting raster when `to` not passed  or is an `Extent`. Otherwise the crs from `to` is used.
  * `boundary`: for polygons, include pixels where the `:center` is inside the polygon,   where the polygon `:touches` the pixel, or that are completely `:inside` the polygon.   The default is `:center`.
  * `shape`: Force `data` to be treated as `:polygon`, `:line` or `:point` geometries.   using points or lines as polygons may have unexpected results.

  * `geometrycolumn`: `Symbol` to manually select the column the geometries are in   when `data` is a Tables.jl compatible table, or a tuple of `Symbol` for columns of   point coordinates.
  * `progress`: show a progress bar, `true` by default, `false` to hide.
  * `vebose`: whether to print messages about potential problems. `true` by default.
  * `threaded`: run operations in parallel, `false` by default. In some circumstances `threaded`    can give large speedups over single-threaded operation. This can be true for complicated    geometries written into low-resolution rasters, but may not be for simple geometries with    high-resolution rasters. With very large rasters threading may be counter productive due    to excessive memory use. Caution should also be used: `threaded` should not be used in in-place    functions writing to `BitArray` or other arrays where race conditions can occur.
  * `threadsafe`: specify that custom `reducer` and/or `op` functions are thread-safe,    in that the order of operation or blocking does not matter. For example,    `sum` and `maximum` are thread-safe, because the answer is approximately (besides   floating point error) the same after running on nested blocks, or on all the data.   In contrast, `median` or `last` are not, because the blocking (`median`) or order (`last`)    matters.
  * `to`: a `Raster`, `RasterStack`, `Tuple` of `Dimension` or `Extents.Extent`.   If no `to` object is provided the extent will be calculated from the geometries,   Additionally, when no `to` object or an `Extent` is passed for `to`, the `size`   or `res` keyword must also be used.
  * `res`: the resolution of the dimensions (often in meters or degrees), a `Real` or `Tuple{<:Real,<:Real}`.   Only required when `to` is not used or is an `Extents.Extent`, and `size` is not used.
  * `size`: the size of the output array, as a `Tuple{Int,Int}` or single `Int` for a square.   Only required when `to` is not used or is an `Extents.Extent`, and `res` is not used.
  * `crs`: a `crs` which will be attached to the resulting raster when `to` not passed  or is an `Extent`. Otherwise the crs from `to` is used.
  * `boundary`: for polygons, include pixels where the `:center` is inside the polygon,   where the polygon `:touches` the pixel, or that are completely `:inside` the polygon.   The default is `:center`.
  * `shape`: Force `data` to be treated as `:polygon`, `:line` or `:point` geometries.   using points or lines as polygons may have unexpected results.

# Example

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, Plots, Dates, Shapefile, GeoInterface, Downloads
using Rasters.Lookups

# Download a borders shapefile
shapefile_url = "https://github.com/nvkelso/natural-earth-vector/raw/master/10m_cultural/ne_10m_admin_0_countries.shp"
shapefile_name = "country_borders.shp"
isfile(shapefile_name) || Downloads.download(shapefile_url, shapefile_name)

# Load the shapes for indonesia
indonesia_border = Shapefile.Handle(shapefile_name).shapes[1]

# Make an empty EPSG 4326 projected Raster of the area of Indonesia
dimz = X(Projected(90.0:0.1:145; sampling=Intervals(), crs=EPSG(4326))),
       Y(Projected(-15.0:0.1:10.9; sampling=Intervals(), crs=EPSG(4326)))

A = zeros(UInt32, dimz; missingval=UInt32(0))

# Rasterize each indonesian island with a different number. The islands are
# rings of a multi-polygon, so we use `GI.getring` to get them all separately.
islands = collect(GeoInterface.getring(indonesia_border))
rasterize!(last, A, islands; fill=1:length(islands), progress=false)

# And plot
p = plot(Rasters.trim(A); color=:spring)
plot!(p, indonesia_border; fillalpha=0, linewidth=0.7)

savefig("build/indonesia_rasterized.png"); nothing

# output

```

![rasterize](indonesia_rasterized.png)

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
