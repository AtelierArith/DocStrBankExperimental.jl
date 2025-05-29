```
ExponentialVariogram(; range, sill, nugget)
```

An exponential variogram with `range` in length units, and `sill` and `nugget` contributions.

```
ExponentialVariogram(; ranges, rotation, sill, nugget)
```

Alternatively, use multiple `ranges` and `rotation` matrix to construct an anisotropic model.

```
ExponentialVariogram(ball; sill, nugget)
```

Alternatively, use a custom metric `ball`.

## Examples

```julia
# isotropic model
ExponentialVariogram(range=2.0m)

# anisotropic model
ExponentialVariogram(ranges=(1.0m, 2.0m))
```
