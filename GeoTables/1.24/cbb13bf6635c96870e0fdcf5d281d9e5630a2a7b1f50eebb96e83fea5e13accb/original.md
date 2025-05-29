```
georef(table, coords; [crs], [lenunit])
```

Georeference `table` using coordinates `coords` of points.

Optionally, specify the coordinate reference system `crs`, which is set by default based on heuristics, and the `lenunit` (default to meters for unitless values) that can only be used in CRS types that allow this flexibility. Any `CRS` or `EPSG`/`ESRI`  code from [CoordRefSystems.jl](https://github.com/JuliaEarth/CoordRefSystems.jl) is supported.

## Examples

```julia
julia> georef((a=[1, 2, 3], b=[4, 5, 6], [(0, 0), (1, 1), (2, 2)])
julia> georef((a=[1, 2, 3], b=[4, 5, 6], [(0, 0), (1, 1), (2, 2)], crs=LatLon)
julia> georef((a=[1, 2, 3], b=[4, 5, 6], [(0, 0), (1, 1), (2, 2)], crs=EPSG{4326})
julia> georef((a=[1, 2, 3], b=[4, 5, 6], [(0, 0), (1, 1), (2, 2)], lenunit=u"cm")
```
