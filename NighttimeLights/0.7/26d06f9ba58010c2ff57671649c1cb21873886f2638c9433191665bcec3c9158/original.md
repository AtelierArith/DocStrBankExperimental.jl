```
readnl(geom, start_date = Date(2012, 04), end_date = Date(2023, 01))
```

Read nighttime lights data from a specific directory and return two raster data cubes representing radiance and coverage. This function also crops the rasters based on the given geometry.

# Arguments

  * `geom`: A geometry object, which will be used to crop the rasters. This could be an instance of `Geometry`, `Polygon`, `MultiPolygon`, etc. from a shapefile.
  * `start_date`: The start date (inclusive) of the period for which to load data. Should be an instance of `Date`. Default is `Date(2012, 04)`.
  * `end_date`: The end date (inclusive) of the period for which to load data. Should be an instance of `Date`. Default is `Date(2023, 01)`.

# Returns

Two `RasterDataCube` instances. The first contains the cropped radiance data, and the second contains the cropped coverage data. Each `RasterDataCube` includes data from the `start_date` to the `end_date`, sorted in ascending order.

# Examples

```julia
using Shapefile
geom = Shapefile.Table("path_to_your_shapefile.shp").geometry[1]  # replace this with your actual shapefile
start_date = Date(2015, 01)
end_date = Date(2020, 12)
rad_dc, cf_dc = readnl(geom, start_date, end_date)
```
