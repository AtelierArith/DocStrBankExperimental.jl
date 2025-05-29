```
georef(table, names; [crs], [lenunit])
```

Georeference `table` using coordinates of points stored in column `names`.

Optionally, specify the coordinate reference system `crs`, which is set by default based on heuristics, and the `lenunit` (default to meters for unitless values) that can only be used in CRS types that allow this flexibility. Any `CRS` or `EPSG`/`ESRI`  code from [CoordRefSystems.jl](https://github.com/JuliaEarth/CoordRefSystems.jl) is supported.

## Examples

```julia
georef((a=rand(10), x=rand(10), y=rand(10)), ("x", "y"))
georef((a=rand(10), x=rand(10), y=rand(10)), ("x", "y"), crs=LatLon)
georef((a=rand(10), x=rand(10), y=rand(10)), ("x", "y"), crs=EPSG{4326})
georef((a=rand(10), x=rand(10), y=rand(10)), ("x", "y"), lenunit=u"cm")
```
