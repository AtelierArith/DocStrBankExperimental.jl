```
GeometrySet(geometries)
```

A set of `geometries` representing a [`Domain`](@ref).

## Examples

Set containing two balls centered at `(0.0, 0.0)` and `(1.0, 1.0)`:

```julia
julia> GeometrySet([Ball((0.0, 0.0)), Ball((1.0, 1.0))])
```

### Notes

Geometries with different CRS will be projected to the CRS of the first geometry.
