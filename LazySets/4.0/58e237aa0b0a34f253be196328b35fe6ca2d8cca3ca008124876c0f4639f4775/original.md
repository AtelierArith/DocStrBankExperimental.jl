# Extended help

```
isbounded(am::AbstractAffineMap; cond_tol::Number=DEFAULT_COND_TOL)
```

### Input

  * `cond_tol` – (optional) tolerance of matrix condition (used to check whether               the matrix is invertible)

### Algorithm

We first check if the matrix is zero or the wrapped set is bounded. If not, we perform a sufficient check whether the matrix is invertible. If the matrix is invertible, then the map being bounded is equivalent to the wrapped set being bounded, and hence the map is unbounded. Otherwise, we check boundedness via [`_isbounded_unit_dimensions`](@ref).
