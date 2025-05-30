```
Raster <: AbsractRaster

Raster(filepath::AbstractString, dims; kw...)
Raster(A::AbstractArray{T,N}, dims; kw...)
Raster(A::AbstractRaster; kw...)
```

A generic [`AbstractRaster`](@ref) for spatial/raster array data. It may hold memory-backed arrays or [`FileArray`](@ref), that simply holds the `String` path to an unopened file. This will only be opened lazily when it is indexed with `getindex` or when `read(A)` is called. Broadcasting, taking a view, reversing and most other  methods *do not* load data from disk: they are applied later, lazily.

# Keywords

  * `dims`: `Tuple` of `Dimension`s for the array.
  * `lazy`: A `Bool` specifying if to load the stack lazily from disk. `false` by default.
  * `name`: `Symbol` name for the array, which will also retreive named layers if `Raster`   is used on a multi-layered file like a NetCDF.
  * `missingval`: value reprsenting missing data, normally detected form the file. Set manually   when you know the value is not specified or is incorrect. This will *not* change any   values in the raster, it simply assigns which value is treated as missing. To replace all of   the missing values in the raster, use [`replace_missing`](@ref).
  * `metadata`: `ArrayMetadata` object for the array, or `NoMetadata()`.
  * `crs`: the coordinate reference system of  the objects `XDim`/`YDim` dimensions.    Only set this if you know the detected crs is incrorrect, or it is not present in   the file. The `crs` is expected to be a GeoFormatTypes.jl `CRS` or `Mixed` `GeoFormat` type.
  * `mappedcrs`: the mapped coordinate reference system of the objects `XDim`/`YDim` dimensions.   for `Mapped` lookups these are the actual values of the index. For `Projected` lookups   this can be used to index in eg. `EPSG(4326)` lat/lon values, having it converted automatically.   Only set this if the detected `mappedcrs` in incorrect, or the file does not have a `mappedcrs`,   e.g. a tiff. The `mappedcrs` is expected to be a GeoFormatTypes.jl `CRS` or `Mixed` `GeoFormat` type.
  * `dropband`: drop single band dimensions. `true` by default.

# Internal Keywords

In some cases it is possible to set these keywords as well.

  * `data`: can replace the data in an `AbstractRaster`
  * `refdims`: `Tuple of` position `Dimension`s the array was sliced from, defaulting to `()`.
