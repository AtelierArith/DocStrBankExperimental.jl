```
SphericalVariogram(; range, sill, nugget)
```

A spherical variogram with `range` in length units, and `sill` and `nugget` contributions.

```
SphericalVariogram(; ranges, rotation, sill, nugget)
```

Alternatively, use multiple `ranges` and `rotation` matrix to construct an anisotropic model.

```
SphericalVariogram(ball; sill, nugget)
```

Alternatively, use a custom metric `ball`.

## Examples

```julia
# isotropic model
SphericalVariogram(range=2.0m)

# anisotropic model
SphericalVariogram(ranges=(1.0m, 2.0m))
```
