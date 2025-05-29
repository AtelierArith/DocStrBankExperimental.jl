```
Raster <: AbstractRaster

Raster(filepath::String; kw...)
Raster(A::AbstractDimArray; kw...)
Raster(A::AbstractArray, dims; kw...)
```

A generic [`AbstractRaster`](@ref) for spatial/raster array data. It can hold  either memory-backed arrays or, if `lazy=true`, a [`FileArray`](@ref),  which stores the `String` path to an unopened file. 

If `lazy=true`, the file will only be opened lazily when it is indexed with `getindex`  or when `read(A)` is called. Broadcasting, taking a view, reversing, and most other  methods will *not* load data from disk; they will be applied later, lazily.

# Arguments

  * `dims`: `Tuple` of `Dimension`s needed when an `AbstractArray` is used.

# Keywords

  * `name`: a `Symbol` name for the array, which will also retrieve the, alphabetically first,    named layer if `Raster` is used on a multi-layered file like a NetCDF.    If instead `RasterStack` is used to read the multi-layered file, by default, all variables    will be added to the stack.
  * `group`: the group in the dataset where `name` can be found. Only needed for nested datasets.   A `String` or `Symbol` will select a single group. Pairs can also used to access groups   at any nested depth, i.e `group=:group1 => :group2 => :group3`.

  * `missingval`: value reprsenting missing data, normally detected from the file. Set manually   when you know the value is not specified or is incorrect. This will *not* change any   values in the raster, it simply assigns which value is treated as missing. To replace all of   the missing values in the raster, use [`replace_missing`](@ref).
  * `metadata`: `Dict` or `Metadata` object for the array, or `NoMetadata()`.
  * `crs`: the coordinate reference system of  the objects `XDim`/`YDim` dimensions.   Only set this if you know the detected crs is incorrect, or it is not present in   the file. The `crs` is expected to be a GeoFormatTypes.jl `CRS` or `Mixed` mode `GeoFormat` object,   like `EPSG(4326)`.

  * `mappedcrs`: the mapped coordinate reference system of the objects `XDim`/`YDim` dimensions.   for `Mapped` lookups these are the actual values of the index. For `Projected` lookups   this can be used to index in eg. `EPSG(4326)` lat/lon values, having it converted automatically.   Only set this if the detected `mappedcrs` in incorrect, or the file does not have a `mappedcrs`,   e.g. a tiff. The `mappedcrs` is expected to be a GeoFormatTypes.jl `CRS` or `Mixed` mode `GeoFormat` type.

  * `refdims`: `Tuple of` position `Dimension`s the array was sliced from, defaulting to `()`.   Usually not needed.

When a filepath `String` is used:

  * `dropband`: drop single band dimensions when creating stacks from filenames. `true` by default.
  * `lazy`: A `Bool` specifying if to load data lazily from disk. `false` by default.
  * `replace_missing`: replace `missingval` with `missing`. This is done lazily if `lazy=true`.   Note that currently for NetCDF and GRIB files `replace_missing` is always true.    In future `replace_missing=false` will also work for these data sources.
  * `source`: Usually automatically detected from filepath extension.    To manually force, a `Symbol` can be passed `:gdal`, `:netcdf`, `:grd`, `:grib`.   The internal [`Rasters.Source`](@ref) objects, such as `Rasters.GDALsource()`,    `Rasters.GRIBsource()` or `Rasters.NCDsource()` can also be used.
  * `write`: defines the default `write` keyword value when calling `open` on the Raster. `false` by default.   Only makes sense to use when `lazy=true`.

When A is an `AbstractDimArray`:

  * `data`: can replace the data in an existing `AbstractRaster`
