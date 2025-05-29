```
underapproximate(X::LazySet, ::Type{<:Ball2})
```

Compute the largest inscribed Euclidean ball in a set `X`.

### Input

  * `X`     – set
  * `Ball2` – target type

### Output

A largest `Ball2` contained in `X`.

### Algorithm

We use `chebyshev_center_radius(X)`.
