# Extended help

```
minkowski_difference(Z1::AbstractZonotope, Z2::AbstractZonotope)
```

### Output

An `HPolytope`.

### Algorithm

For one-dimensional sets, this method implements a simple algorithm for intervals. For two-dimensional sets, this method implements [Althoff15; Proposition 6](@citet). For higher-dimensional sets, this method implements [Althoff15; Theorem 3](@citet).
