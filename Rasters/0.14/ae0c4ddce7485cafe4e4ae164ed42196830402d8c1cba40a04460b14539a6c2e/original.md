```
RasterSeries <: AbstractRasterSeries

RasterSeries(rasters::AbstractArray{<:AbstractRaster}, dims; [refdims])
RasterSeries(stacks::AbstractArray{<:AbstractRasterStack}, dims; [refdims]) 

RasterSeries(paths::AbstractArray{<:AbstractString}, dims; child, duplicate_first, kw...)
RasterSeries(path:::AbstractString, dims; ext, separator, child, duplicate_first, kw...)

RasterSeries(objects::AbstractBasicDimArray; kw...)
```

Concrete implementation of [`AbstractRasterSeries`](@ref).

A `RasterSeries` is an array of `Raster`s or `RasterStack`s, along some dimension(s).

Existing `Raster` `RasterStack` can be wrapped in a `RasterSeries`, or new files  can be loaded from an array of `String` or from a single `String`.

A single `String` can refer to a whole directory, or the name of a series of files in a directory, sharing a common stem. The differnce between the filenames can be used as the lookup for the series. 

For example, with some tifs at these paths : 

```
"series_dir/myseries_2001-01-01T00:00:00.tif"
"series_dir/myseries_2002-01-01T00:00:00.tif"
```

We can load a `RasterSeries` with a `DateTime` lookup:

```julia
julia> ser = RasterSeries("series_dir/myseries.tif", Ti(DateTime))
2-element RasterSeries{Raster,1} with dimensions: 
  Ti Sampled{DateTime} DateTime[DateTime("2001-01-01T00:00:00"), DateTime("2002-01-01T00:00:00")] ForwardOrdered Irregular Points
```

The `DateTime` suffix is parsed from the filenames. Using `Ti(Int)` would try to parse integers instead.

Just using the directory will also work, unless there are other files mixed in it:

```julia
julia> ser = RasterSeries("series_dir", Ti(DateTime))
2-element RasterSeries{Raster,1} with dimensions: 
  Ti Sampled{DateTime} DateTime[DateTime("2001-01-01T00:00:00"), DateTime("2002-01-01T00:00:00")] ForwardOrdered Irregular Points
```

# Arguments

  * `dims`: series dimension/s.

# Keywords

When loading a series from a Vector of `String` paths or a single `String` path:

  * `child`: constructor of child objects for use when filenames are passed in,   can be `Raster` or `RasterStack`. Defaults to `Raster`.
  * `duplicate_first::Bool`: wether to duplicate the dimensions and metadata of the   first file with all other files. This can save load time with a large   series where dimensions are identical. `false` by default.
  * `lazy`: A `Bool` specifying if to load data lazily from disk. `false` by default.
  * `kw`: keywords passed to the child constructor [`Raster`](@ref) or [`RasterStack`](@ref).

When loading a series from a single `String` path:

  * `separator`: separator used to split lookup elements from the rest of a filename. '_' by default.

Others:

  * `refdims`: existing reference dimension/s, normally not required.
