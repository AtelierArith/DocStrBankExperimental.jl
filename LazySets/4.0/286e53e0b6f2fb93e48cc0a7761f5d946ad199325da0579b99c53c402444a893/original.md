```
σ(d::AbstractVector, R::Rectification)
```

Return a support vector of a rectification.

### Input

  * `d` – direction
  * `R` – rectification

### Output

A support vector in the given direction. If the direction has norm zero, the result depends on the wrapped set.
