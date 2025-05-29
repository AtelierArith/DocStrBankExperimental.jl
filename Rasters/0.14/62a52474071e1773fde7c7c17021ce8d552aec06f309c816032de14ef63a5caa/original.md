```
RasterStack <: AbstrackRasterStack

RasterStack(data...; name, kw...)
RasterStack(data::Union{Vector,Tuple}; name, kw...)
RasterStack(data::NamedTuple; kw...))
RasterStack(data::RasterStack; kw...)
RasterStack(data::Raster; layersfrom=Band, kw...)
RasterStack(filepath::AbstractString; kw...)
```

Load a file path or a `NamedTuple` of paths as a `RasterStack`, or convert arguments, a `Vector` or `NamedTuple` of `Raster`s to `RasterStack`.

# Arguments

  * `data`: A `NamedTuple` of [`Raster`](@ref)s or `String`, or a `Vector`, `Tuple` or splatted   arguments of [`Raster`](@ref). The latter options must pass a `name` keyword argument.
  * `filepath`: A file (such as netcdf or tif) to be loaded as a stack, or a directory path   containing multiple files.

# Keywords

  * `name`: Used as stack layer names when a `Tuple`, `Vector` or splat of `Raster` is passed in.   Has no effect when `NameTuple` is used - the `NamedTuple` keys are the layer names.
  * `group`: the group in the dataset where `name` can be found. Only needed for nested datasets.   A `String` or `Symbol` will select a single group. Pairs can also used to access groups   at any nested depth, i.e `group=:group1 => :group2 => :group3`.
  * `metadata`: A `Dict` or `DimensionalData.Metadata` object.
  * `missingval`: value representing missing data, normally detected from the file and    automatically converted to `missing`. Setting to an alternate value, such as `0`    or `NaN` may be desirable for improved perfomance. `nothing` specifies no missing value.    Using the same `missingval` the file already has removes the overhead of replacing it,   this can be done by passing the `missingval` function as `missingval`.    If the file has an incorrect value, we can manually define the transformation   as a pair like `correct_value => missing` or `correct_value => NaN`.   `correct_value => correct_value` will keep remove the overhead of changing it.    Note: When `raw=true` is set, `missingval` is not changed from the value specified   in the file.

    For `RasterStack` a `NamedTuple` can also be passed if layers   should have different `missingval`.
  * `crs`: the coordinate reference system of  the objects `XDim`/`YDim` dimensions.   Only set this if you know the detected crs is incorrect, or it is not present in   the file. The `crs` is expected to be a GeoFormatTypes.jl `CRS` or `Mixed` mode `GeoFormat` object,   like `EPSG(4326)`.
  * `mappedcrs`: the mapped coordinate reference system of the objects `XDim`/`YDim` dimensions.   for `Mapped` lookups these are the actual values of the index. For `Projected` lookups   this can be used to index in eg. `EPSG(4326)` lat/lon values, having it converted automatically.   Only set this if the detected `mappedcrs` in incorrect, or the file does not have a `mappedcrs`,   e.g. a tiff. The `mappedcrs` is expected to be a GeoFormatTypes.jl `CRS` or `Mixed` mode `GeoFormat` type.
  * `refdims`: `Tuple` of `Dimension` that the stack was sliced from.

For when one or multiple filepaths are used:

  * `dropband`: drop single band dimensions when creating stacks from filenames. `true` by default.
  * `lazy`: A `Bool` specifying if to load data lazily from disk. `false` by default.
  * `raw`: turn of all scaling and masking and load the raw values from disk.   `false` by default. If `true`, `scaled` will be set to `false` and `missingval`   will to the existing missing value in the file. A warning will be printed if    `scaled` or `missingval` are manually set to another value.
  * `scaled`: apply scale and offset as `x * scale + offset` where    `scale` and/or `offset` are found in file metadata. `true` by default.   This is common where data has been convert to e.g. UInt8 to save disk space.   To ignore `scale` and `offset` metadata, use `scaled=false`.    Note 1: If `scale` and `offset` are `1.0` and `0.0` they will be ignored and the    original type will be used even when `scaled=true`. This is because these values    may be fallback defaults and we do not want to convert every `Real` array to larger   `Float64` values.    Note 2: `raw=true` will ignore `scaled` and `missingval` and return   the raw values.
  * `source`: Usually automatically detected from filepath extension.    To manually force, a `Symbol` can be passed `:gdal`, `:netcdf`, `:grd`, `:grib`.   The internal [`Rasters.Source`](@ref) objects, such as `Rasters.GDALsource()`,    `Rasters.GRIBsource()` or `Rasters.NCDsource()` can also be used.

For when a single `Raster` is used:

  * `layersfrom`: `Dimension` to source stack layers from if the file is not already multi-layered.   `nothing` is default, so that a single `RasterStack(raster)` is a single layered stack.   `RasterStack(raster; layersfrom=Band)` will use the bands as layers.

```julia
files = (temp="temp.tif", pressure="pressure.tif", relhum="relhum.tif")
stack = RasterStack(files; mappedcrs=EPSG(4326))
stack[:relhum][Lat(Contains(-37), Lon(Contains(144))
```
