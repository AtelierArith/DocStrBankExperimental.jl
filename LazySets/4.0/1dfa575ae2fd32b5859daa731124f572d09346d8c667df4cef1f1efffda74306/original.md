# Extended help

```
volume(am::AbstractAffineMap)
```

### Notes

This implementation requires a dimension-preserving map (i.e., a square matrix).

### Algorithm

A square linear map scales the volume of any set by its absolute determinant. A translation does not affect the volume. Thus, the volume of `M * X + {v}` is `|det(M)| * volume(X)`.
