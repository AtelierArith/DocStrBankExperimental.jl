```
LineSource(p, line)
```

Create a line irradiance source geometry given an origin (`p`) and a segment (`line`) both specified as vector of Cartesian coordinates (`Vec(x, y, z)`). This will create a line source between the points `p` and `p .+ line`.

## Examples

```jldoctest
julia> import PlantGeomPrimitives as PG

julia> source_geom = LineSource(PG.Vec(1.0, 1.0, 1.0), PG.Y());
```
