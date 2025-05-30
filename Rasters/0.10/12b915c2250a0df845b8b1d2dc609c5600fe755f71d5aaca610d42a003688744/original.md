```
RasterStack <: AbstrackRasterStack

RasterStack(data...; name, kw...)
RasterStack(data::Union{Vector,Tuple}; name, kw...)
RasterStack(data::NamedTuple; kw...))
RasterStack(s::AbstractRasterStack; kw...)
RasterStack(s::AbstractRaster; layersfrom=Band, kw...)
RasterStack(filename::AbstractString; kw...)
```

Load a file path or a `NamedTuple` of paths as a `RasterStack`, or convert arguments, a `Vector` or `NamedTuple` of `Raster`s to `RasterStack`.

# Arguments

  * `data`: A `NamedTuple` of [`Raster`](@ref)s, or a `Vector`, `Tuple` or splatted arguments   of [`Raster`](@ref). The latter options must pass a `name` keyword argument.
  * `filename`: A file (such as netcdf or tif) to be loaded as a stack, or a directory path   containing multiple files.

# Keywords

  * `name`: Used as stack layer names when a `Tuple`, `Vector` or splat of `Raster` is passed in.   Has no effect when `NameTuple` is used - the `NamedTuple` keys are the layer names.
  * `metadata`: A `Dict` or `DimensionalData.Metadata` object.
  * `refdims`: `Tuple` of `Dimension` that the stack was sliced from.
  * `layersfrom`: `Dimension` to source stack layers from if the file is not already multi-layered.   `nothing` is default, so that a single `RasterStack(raster)` is a single layered stack.   `RasterStack(raster; layersfrom=Band)` will use the bands as layers.
  * `lazy`: A `Bool` specifying whether to load the stack lazily from disk. `false` by default.
  * `dropband`: drop single band dimensions when creating stacks from filenames. `true` by default.

```julia
files = (temp="temp.tif", pressure="pressure.tif", relhum="relhum.tif")
stack = RasterStack(files; mappedcrs=EPSG(4326))
stack[:relhum][Lat(Contains(-37), Lon(Contains(144))
```
