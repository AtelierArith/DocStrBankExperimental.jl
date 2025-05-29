```
PointSource(vec)
```

Create a point irradiance source geometry at given 3D location `vec`, defined as vector of Cartesian coordinates (`Vec(x, y, z)`).

## Examples

```jldoctest
julia> import PlantGeomPrimitives as PG

julia> source_geom = PointSource(PG.Vec(1.0, 1.0, 1.0));
```
