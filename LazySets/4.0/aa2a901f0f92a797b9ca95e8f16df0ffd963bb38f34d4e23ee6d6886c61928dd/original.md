# Extended help

```
minkowski_sum(PZ::DensePolynomialZonotope, Z::AbstractZonotope)
```

## Output

A `DensePolynomialZonotope`.

### Algorithm

The polynomial zonotope's center is the sum of the centers of `PZ` and `Z`, and its generators are the concatenation of the generators of `PZ` and `Z`.
