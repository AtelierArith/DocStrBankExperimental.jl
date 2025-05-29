```
σ(d::AbstractVector, rm::ResetMap)
```

Return a support vector of a reset map.

### Input

  * `d`  – direction
  * `rm` – reset map

### Output

A support vector in the given direction. If the direction has norm zero, the result depends on the wrapped set.
