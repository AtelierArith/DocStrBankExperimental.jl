```
crop(x; to, touches=false, atol=0, [geometrycolumn])
crop(xs...; to)
```

Crop one or multiple [`AbstractRaster`](@ref) or [`AbstractRasterStack`](@ref) `x` to match the size of the object `to`, or smallest of any dimensions that are shared.

`crop` is lazy, using a `view` into the object rather than allocating new memory.

# Keywords

  * `to`: the object to crop to. This can be a [`Raster`](@ref) or one or multiple geometries. Geometries can be   a GeoInterface.jl `AbstractGeometry`, a nested `Vector` of `AbstractGeometry`,   or a Tables.jl compatible object containing a `:geometry` column or points and values columns,   in which case `geometrycolumn` must be specified. If no `to` keyword is passed, the smallest shared area of all `xs` is used.
  * `touches`: `true` or `false`. Whether to use `Touches` wraper on the object extent.  When lines need to be included in e.g. zonal statistics, `true` should be used.
  * `atol`: the absolute tolerance to use when cropping to an extent. If edges are less than   `atol` away from the extent of `to`, they are included.
  * `geometrycolumn`: `Symbol` to manually select the column the geometries are in   when `data` is a Tables.jl compatible table, or a tuple of `Symbol` for columns of   point coordinates.

As `crop` is lazy, `filename` and `suffix` keywords are not used.

# Example

Crop to another raster:

```jldoctest
using Rasters, RasterDataSources, Plots
evenness = Raster(EarthEnv{HabitatHeterogeneity}, :evenness)
rnge = Raster(EarthEnv{HabitatHeterogeneity}, :range)

# Roughly cut out New Zealand from the evenness raster
nz_bounds = X(165 .. 180), Y(-50 .. -32)
nz_evenness = evenness[nz_bounds...]

# Crop range to match evenness
nz_range = crop(rnge; to=nz_evenness)
plot(nz_range)

savefig("build/nz_crop_example.png");
nothing

# output
```

![new zealand evenness cropped](nz_crop_example.png)

Crop to a polygon:

```jldoctest
using Rasters, RasterDataSources, Plots, Dates, Shapefile, Downloads

# Download a borders shapefile
shapefile_url = "https://github.com/nvkelso/natural-earth-vector/raw/master/10m_cultural/ne_10m_admin_0_countries.shp"
shapefile_name = "boundary.shp"
isfile(shapefile_name) || Downloads.download(shapefile_url, shapefile_name)
shp = Shapefile.Handle(shapefile_name).shapes[6]

evenness = Raster(EarthEnv{HabitatHeterogeneity}, :evenness)
argentina_evenness = crop(evenness; to=shp)
plot(argentina_evenness)

savefig("build/argentina_crop_example.png"); nothing

# output
```

![argentina evenness cropped](argentina_crop_example.png)

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
