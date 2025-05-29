```
rasterize([reducer], data; geometrycolumn, kw...)
```

Rasterize a GeoInterface.jl compatable geometry or feature, or a Tables.jl table with a `:geometry` column of GeoInterface.jl objects, or points columns specified by `geometrycolumn`

# Arguments

  * `reducer`: a reducing function to reduce the fill value for all geometries that   cover or touch a pixel down to a single value. The default is `last`.   Any  that takes an iterable and returns a single value will work, including   custom functions. However, there are optimisations for built-in methods   including `sum`, `first`, `last`, `minimum`, `maximum`, `extrema` and `Statistics.mean`.   These may be an order of magnitude or more faster than   `count` is a special-cased as it does not need a fill value.
  * `data`: a GeoInterface.jl `AbstractGeometry`, a nested `Vector` of `AbstractGeometry`,   or a Tables.jl compatible object containing a `:geometry` column or points and values columns,   in which case `geometrycolumn` must be specified.

# Keywords

These are detected automatically from `data` where possible.

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
  * `filename`: a filename to write to directly, useful for large files.
  * `suffix`: a string or value to append to the filename.   A tuple of `suffix` will be applied to stack layers. `keys(stack)` are the default.

Note on threading. Performance may be much better with `threaded=false` if `reducer`/`op` are not `threadsafe`. `sum`, `prod`, `maximum`, `minimum` `count` and `mean` (by combining `sum` and `count`) are threadsafe. If you know your algorithm is threadsafe, use `threadsafe=true` to allow all optimisations. Functions passed to `fill` are always threadsafe, and ignore the `threadsafe` argument.

# Example

Rasterize a shapefile for China and plot, with a border.

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, Plots, Dates, Shapefile, Downloads
using Rasters.Lookups

# Download a borders shapefile
shapefile_url = "https://github.com/nvkelso/natural-earth-vector/raw/master/10m_cultural/ne_10m_admin_0_countries.shp"
shapefile_name = "country_borders.shp"
isfile(shapefile_name) || Downloads.download(shapefile_url, shapefile_name)

# Load the shapes for china
china_border = Shapefile.Handle(shapefile_name).shapes[10]

# Rasterize the border polygon
china = rasterize(last, china_border; res=0.1, missingval=0, fill=1, boundary=:touches, progress=false)

# And plot
p = plot(china; color=:spring, legend=false)
plot!(p, china_border; fillalpha=0, linewidth=0.6)

savefig("build/china_rasterized.png"); nothing

# output

```

![rasterize](china_rasterized.png)

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
