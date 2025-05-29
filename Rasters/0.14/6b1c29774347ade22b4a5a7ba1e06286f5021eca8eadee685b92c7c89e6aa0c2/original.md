```
Raster <: AbstractRaster

Raster(filepath::String; kw...)
Raster(A::AbstractDimArray; kw...)
Raster(A::AbstractArray, dims; kw...)
```

A generic [`AbstractRaster`](@ref) for spatial/raster array data. It can hold either memory-backed arrays or, if `lazy=true`, a [`FileArray`](@ref), which stores the `String` path to an unopened file.

If `lazy=true`, the file will only be opened lazily when it is indexed with `getindex` or when `read(A)` is called. Broadcasting, taking a view, reversing, and most other methods will *not* load data from disk; they will be applied later, lazily.

# Arguments

  * `dims`: `Tuple` of `Dimension`s needed when an `AbstractArray` is used.

# Keywords

  * `name`: a `Symbol` name for a Raster, which will also retrieve the    a named layer if `Raster` is used on a multi-layered file like a NetCDF.
  * `group`: the group in the dataset where `name` can be found. Only needed for nested datasets.   A `String` or `Symbol` will select a single group. Pairs can also used to access groups   at any nested depth, i.e `group=:group1 => :group2 => :group3`.
  * `missingval`: value representing missing data, normally detected from the file and    automatically converted to `missing`. Setting to an alternate value, such as `0`    or `NaN` may be desirable for improved perfomance. `nothing` specifies no missing value.    Using the same `missingval` the file already has removes the overhead of replacing it,   this can be done by passing the `missingval` function as `missingval`.    If the file has an incorrect value, we can manually define the transformation   as a pair like `correct_value => missing` or `correct_value => NaN`.   `correct_value => correct_value` will keep remove the overhead of changing it.    Note: When `raw=true` is set, `missingval` is not changed from the value specified   in the file.
  * `metadata`: `Dict` or `Metadata` object for the array, or `NoMetadata()`.
  * `crs`: the coordinate reference system of  the objects `XDim`/`YDim` dimensions.   Only set this if you know the detected crs is incorrect, or it is not present in   the file. The `crs` is expected to be a GeoFormatTypes.jl `CRS` or `Mixed` mode `GeoFormat` object,   like `EPSG(4326)`.
  * `mappedcrs`: the mapped coordinate reference system of the objects `XDim`/`YDim` dimensions.   for `Mapped` lookups these are the actual values of the index. For `Projected` lookups   this can be used to index in eg. `EPSG(4326)` lat/lon values, having it converted automatically.   Only set this if the detected `mappedcrs` in incorrect, or the file does not have a `mappedcrs`,   e.g. a tiff. The `mappedcrs` is expected to be a GeoFormatTypes.jl `CRS` or `Mixed` mode `GeoFormat` type.
  * `refdims`: `Tuple of` position `Dimension`s the array was sliced from, defaulting to `()`.   Usually not needed.

When a filepath `String` is used:

  * `dropband`: drop single band dimensions when creating stacks from filenames. `true` by default.
  * `lazy`: A `Bool` specifying if to load data lazily from disk. `false` by default.
  * `source`: Usually automatically detected from filepath extension.    To manually force, a `Symbol` can be passed `:gdal`, `:netcdf`, `:grd`, `:grib`.   The internal [`Rasters.Source`](@ref) objects, such as `Rasters.GDALsource()`,    `Rasters.GRIBsource()` or `Rasters.NCDsource()` can also be used.
  * `scaled`: apply scale and offset as `x * scale + offset` where    `scale` and/or `offset` are found in file metadata. `true` by default.   This is common where data has been convert to e.g. UInt8 to save disk space.   To ignore `scale` and `offset` metadata, use `scaled=false`.    Note 1: If `scale` and `offset` are `1.0` and `0.0` they will be ignored and the    original type will be used even when `scaled=true`. This is because these values    may be fallback defaults and we do not want to convert every `Real` array to larger   `Float64` values.    Note 2: `raw=true` will ignore `scaled` and `missingval` and return   the raw values.
  * `raw`: turn of all scaling and masking and load the raw values from disk.   `false` by default. If `true`, `scaled` will be set to `false` and `missingval`   will to the existing missing value in the file. A warning will be printed if    `scaled` or `missingval` are manually set to another value.

When A is an `AbstractDimArray`:

  * `data`: can replace the data in an existing `AbstractRaster`
