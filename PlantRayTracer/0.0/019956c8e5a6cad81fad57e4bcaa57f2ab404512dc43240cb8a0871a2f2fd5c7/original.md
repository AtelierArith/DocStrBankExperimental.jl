```
FixedSource(dir)
FixedSource(θ, Φ)
```

Create a fixed irradiance source by given a vector with the direction of the rays (dir) or zenith (θ) and azimuth (Φ) angles.

## Examples

```jldoctest
julia> source_dir = FixedSource(0.0, 0.0);

julia> import PlantGeomPrimitives as PG

julia> source_dir = FixedSource(PG.Vec(0.0, 0.0, -1.0));
```
