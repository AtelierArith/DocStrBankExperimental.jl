```
extract(x, geometries; kw...)
```

Extracts the value of `Raster` or `RasterStack` for the passed in geometries, returning an `Vector{NamedTuple}` with properties for `:geometry` and `Raster` or `RasterStack` layer values.

For lines, linestrings and linear rings points are extracted for each pixel that the line touches.

For polygons, all cells witih centers covered by the polygon are returned.

Note that if objects have more dimensions than the length of the point tuples, sliced arrays or stacks will be returned instead of single values.

# Arguments

  * `x`: a `Raster` or `RasterStack` to extract values from.
  * `data`: a GeoInterface.jl `AbstractGeometry`, a nested `Vector` of `AbstractGeometry`,   or a Tables.jl compatible object containing a `:geometry` column or points and values columns,   in which case `geometrycolumn` must be specified.

# Keywords

  * `geometry`: include a `:geometry` field in rows, which will be a   tuple point. Either the original point for points or the pixel   center point for line and polygon extract. `true` by default.
  * `index`: include `:index` field of extracted points in rows, `false` by default.
  * `name`: a `Symbol` or `Tuple` of `Symbol` corresponding to layer/s   of a `RasterStack` to extract. All layers are extracted by default.
  * `skipmissing`: skip missing points automatically.
  * `flatten`: flatten extracted points from multiple    geometries into a single vector. `true` by default.    Unmixed point geometries are always flattened.   Flattening is slow and single threaded, `flatten=false` may be a    large performance improvement in combination with `threaded=true`.
  * `atol`: a tolerance for floating point lookup values for when the `Lookup`   contains `Points`. `atol` is ignored for `Intervals`.
  * `boundary`: for polygons, include pixels where the `:center` is inside the polygon,   where the polygon `:touches` the pixel, or that are completely `:inside` the polygon.   The default is `:center`.
  * `geometrycolumn`: `Symbol` to manually select the column the geometries are in   when `data` is a Tables.jl compatible table, or a tuple of `Symbol` for columns of   point coordinates.

# Example

Here we extract points matching the occurrence of the Mountain Pygmy Possum, *Burramis parvus*. This could be used to fit a species distribution model.

```julia
using Rasters, RasterDataSources, ArchGDAL, GBIF2, CSV

# Get a stack of BioClim layers, and replace missing values with `missing`
st = RasterStack(WorldClim{BioClim}, (1, 3, 5, 7, 12)) |> replace_missing

# Download some occurrence data
obs = GBIF2.occurrence_search("Burramys parvus"; limit=5, year="2009")

# use `extract` to get values for all layers at each observation point.
# We `collect` to get a `Vector` from the lazy iterator.
extract(st, obs; skipmissing=true)

# output
5-element Vector{NamedTuple{(:geometry, :bio1, :bio3, :bio5, :bio7, :bio12)}}:
 (geometry = (0.21, 40.07), bio1 = 17.077084f0, bio3 = 41.20417f0, bio5 = 30.1f0, bio7 = 24.775f0, bio12 = 446.0f0)
 (geometry = (0.03, 39.97), bio1 = 17.076923f0, bio3 = 39.7983f0, bio5 = 29.638462f0, bio7 = 24.153847f0, bio12 = 441.0f0)
 (geometry = (0.03, 39.97), bio1 = 17.076923f0, bio3 = 39.7983f0, bio5 = 29.638462f0, bio7 = 24.153847f0, bio12 = 441.0f0)
 (geometry = (0.52, 40.37), bio1 = missing, bio3 = missing, bio5 = missing, bio7 = missing, bio12 = missing)
 (geometry = (0.32, 40.24), bio1 = 16.321388f0, bio3 = 41.659454f0, bio5 = 30.029825f0, bio7 = 25.544561f0, bio12 = 480.0f0)
```

Note: passing in arrays, geometry collections or feature collections containing a mix of points and other geometries has undefined results.
