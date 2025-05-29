```
CircularVariogram(; range, sill, nugget)
```

A circular variogram with `range` in length units, and `sill` and `nugget` contributions.

```
CircularVariogram(; ranges, rotation, sill, nugget)
```

Alternatively, use multiple `ranges` and `rotation` matrix to construct an anisotropic model.

```
CircularVariogram(ball; sill, nugget)
```

Alternatively, use a custom metric `ball`.

## Examples

```julia
# isotropic model
CircularVariogram(range=2.0m)

# anisotropic model
CircularVariogram(ranges=(1.0m, 2.0m))
```
