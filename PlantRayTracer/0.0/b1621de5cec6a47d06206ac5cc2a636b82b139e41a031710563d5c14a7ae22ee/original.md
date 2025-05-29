```
Source(geom, angle, power::Number, nrays)
Source(geom, angle, power::Tuple, nrays)
```

Create an irradiance source given a source geometry, a source angle, the power per ray and the total number of rays to be generated from this source. When simulating more than one wavelength simultaneously, a tuple of power values should be given, of the same length as in the materials used in the scene. See VPL documentation for details on source geometries and source angles.

## Examples

```jldoctest
julia> import PlantGeomPrimitives as PG

julia> source_geom = PointSource(PG.O());

julia> source_dir = FixedSource(0.0, 0.0);

julia> Source(source_geom, source_dir, 1.0, 1_000);
```
