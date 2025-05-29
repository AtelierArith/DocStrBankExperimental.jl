```
LambertianSource(x, y, z)
LambertianSource(axes)
```

Create a Lambertian irradiance source angle by given a local coordinate system as three separate `Vec` objects representing the axes (x, y, z) or as tuple containing the three axes. Rays will be generated towards the hemisphere defined by the `z` direction. See VPL documentation for details on irradiance sources.

## Examples

```jldoctest
julia> import PlantGeomPrimitives as PG

julia> source_dir = LambertianSource(PG.X(), PG.Y(), PG.Z());

julia> source_dir = LambertianSource((PG.X(), PG.Y(), PG.Z()));
```
