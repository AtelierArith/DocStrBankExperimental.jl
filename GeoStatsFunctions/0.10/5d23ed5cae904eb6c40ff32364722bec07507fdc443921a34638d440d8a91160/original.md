```
SineHoleVariogram(; range, sill, nugget)
```

A sinehole variogram with `range` in length units, and `sill` and `nugget` contributions.

```
SineHoleVariogram(; ranges, rotation, sill, nugget)
```

Alternatively, use multiple `ranges` and `rotation` matrix to construct an anisotropic model.

```
SineHoleVariogram(ball; sill, nugget)
```

Alternatively, use a custom metric `ball`.

## Examples

```julia
# isotropic model
SineHoleVariogram(range=2.0m)

# anisotropic model
SineHoleVariogram(ranges=(1.0m, 2.0m))
```
