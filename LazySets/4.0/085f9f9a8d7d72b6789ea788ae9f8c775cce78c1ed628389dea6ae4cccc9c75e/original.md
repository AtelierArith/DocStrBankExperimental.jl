```
σ(d::AbstractVector, cp::CartesianProduct)
```

Return a support vector of a Cartesian product.

### Input

  * `d`  – direction
  * `cp` – Cartesian product

### Output

A support vector in the given direction. If the direction has norm zero, the result depends on the wrapped sets.
