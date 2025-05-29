```
CubicVariogram(; range, sill, nugget)
```

A cubic variogram with `range` in length units, and `sill` and `nugget` contributions.

```
CubicVariogram(; ranges, rotation, sill, nugget)
```

Alternatively, use multiple `ranges` and `rotation` matrix to construct an anisotropic model.

```
CubicVariogram(ball; sill, nugget)
```

Alternatively, use a custom metric `ball`.

## Examples

```julia
# isotropic model
CubicVariogram(range=2.0m)

# anisotropic model
CubicVariogram(ranges=(1.0m, 2.0m))
```
