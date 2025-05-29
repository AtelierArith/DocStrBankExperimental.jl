```
PentaSphericalVariogram(; range, sill, nugget)
```

A pentaspherical variogram with `range` in length units, and `sill` and `nugget` contributions.

```
PentaSphericalVariogram(; ranges, rotation, sill, nugget)
```

Alternatively, use multiple `ranges` and `rotation` matrix to construct an anisotropic model.

```
PentaSphericalVariogram(ball; sill, nugget)
```

Alternatively, use a custom metric `ball`.

## Examples

```julia
# isotropic model
PentaSphericalVariogram(range=2.0m)

# anisotropic model
PentaSphericalVariogram(ranges=(1.0m, 2.0m))
```
