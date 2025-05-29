# Extended help

```
linear_map(M::AbstractMatrix, Z::AbstractZonotope)
```

### Output

A `Zonotope`.

### Algorithm

We apply the linear map to the center and the generators.

If the map has outpu dimension 1, a specialized algorithm ensures that the resulting zonotope only has a single generator.
