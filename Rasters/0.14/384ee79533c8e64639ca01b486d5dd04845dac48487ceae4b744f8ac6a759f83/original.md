```
zonal(f, x::Union{Raster,RasterStack}; of, kw...)
```

Calculate zonal statistics for the the zone of a `Raster` or `RasterStack` covered by the `of` object/s.

# Arguments

  * `f`: any function that reduces an iterable to a single value, such as `sum` or `Statistics.mean`
  * `x`: A `Raster` or `RasterStack`
  * `of`: A `DimTuple`, `Extent`, a [`Raster`](@ref) or one or multiple geometries. Geometries can be   a GeoInterface.jl `AbstractGeometry`, a nested `Vector` of `AbstractGeometry`,   or a Tables.jl compatible object containing a `:geometry` column or points and values columns,   in which case `geometrycolumn` must be specified.

# Keywords

  * `geometrycolumn`: `Symbol` to manually select the column the geometries are in   when `data` is a Tables.jl compatible table, or a tuple of `Symbol` for columns of   point coordinates.

These can be used when `of` is or contains (a) GeoInterface.jl compatible object(s):

  * `shape`: Force `data` to be treated as `:polygon`, `:line` or `:point`, where possible.
  * `boundary`: for polygons, include pixels where the `:center` is inside the polygon,   where the line `:touches` the pixel, or that are completely `:inside` inside the polygon.   The default is `:center`.
  * `progress`: show a progress bar, `true` by default, `false` to hide..
  * `skipmissing`: wether to apply `f` to the result of `skipmissing(A)` or not. If `true`   `f` will be passed an iterator over the values, which loses all spatial information.   if `false` `f` will be passes a masked `Raster` or `RasterStack`, and will be responsible   for handling missing values itself. The default value is `true`.

# Example

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, DataFrames, Statistics, Dates, NaturalEarth
# Download borders
countries = naturalearth("admin_0_countries", 10) |> DataFrame
# Download and read a raster stack from WorldClim
st = RasterStack(WorldClim{Climate}; month=Jan)
# Calculate the january mean of all climate variables for all countries
january_stats = zonal(mean, st; of=countries, boundary=:touches, progress=false) |> DataFrame
# Add the country name column (natural earth has some string errors it seems)
insertcols!(january_stats, 1, :country => first.(split.(countries.ADMIN, r"[^A-Za-z ]")))
# output
258×8 DataFrame
 Row │ country                       tmin       tmax       tavg       prec     ⋯
     │ SubStrin…                     Float32    Float32    Float32    Float64  ⋯
─────┼──────────────────────────────────────────────────────────────────────────
   1 │ Indonesia                      21.5447    29.1865    25.3656   271.063  ⋯
   2 │ Malaysia                       21.3087    28.4291    24.8688   273.381
   3 │ Chile                           7.24534   17.9262    12.5858    78.1287
   4 │ Bolivia                        17.2065    27.7454    22.4758   192.542
   5 │ Peru                           15.0273    25.5504    20.2889   180.007  ⋯
   6 │ Argentina                      13.6751    27.6716    20.6732    67.1837
   7 │ Dhekelia Sovereign Base Area    5.87126   15.8991    10.8868    76.25
   8 │ Cyprus                          5.65921   14.6665    10.1622    97.4474
  ⋮  │              ⋮                    ⋮          ⋮          ⋮         ⋮     ⋱
 252 │ Spratly Islands                25.0       29.2       27.05      70.5    ⋯
 253 │ Clipperton Island              21.5       33.2727    27.4        6.0
 254 │ Macao S                        11.6694    17.7288    14.6988    28.0
 255 │ Ashmore and Cartier Islands   NaN        NaN        NaN        NaN
 256 │ Bajo Nuevo Bank               NaN        NaN        NaN        NaN      ⋯
 257 │ Serranilla Bank               NaN        NaN        NaN        NaN
 258 │ Scarborough Reef              NaN        NaN        NaN        NaN
                                                  3 columns and 243 rows omitted
```
