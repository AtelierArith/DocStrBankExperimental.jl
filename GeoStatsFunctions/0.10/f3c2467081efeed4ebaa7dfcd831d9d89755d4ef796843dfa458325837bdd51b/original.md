```
MaternVariogram(; range, sill, nugget, order)
```

A Matérn variogram with `range` in length units, `sill` and `nugget` contributions, and `order` of Bessel function.

```
MaternVariogram(; ranges, rotation, sill, nugget, order)
```

Alternatively, use multiple `ranges` and `rotation` matrix to construct an anisotropic model.

```
MaternVariogram(ball; sill, nugget, order)
```

Alternatively, use a custom metric `ball`.

## Examples

```julia
# isotropic model
MaternVariogram(range=2.0m)

# anisotropic model
MaternVariogram(ranges=(1.0m, 2.0m))
```
