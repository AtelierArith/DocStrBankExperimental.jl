```
GaussianVariogram(; range, sill, nugget)
```

A Gaussian variogram with `range` in length units, and `sill` and `nugget` contributions.

```
GaussianVariogram(; ranges, rotation, sill, nugget)
```

Alternatively, use multiple `ranges` and `rotation` matrix to construct an anisotropic model.

```
GaussianVariogram(ball; sill, nugget)
```

Alternatively, use a custom metric `ball`.

## Examples

```julia
# isotropic model
GaussianVariogram(range=2.0m)

# anisotropic model
GaussianVariogram(ranges=(1.0m, 2.0m))
```
