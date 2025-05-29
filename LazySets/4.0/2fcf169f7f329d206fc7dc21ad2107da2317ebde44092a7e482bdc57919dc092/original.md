```
σ(d::AbstractVector, sih::SymmetricIntervalHull)
```

Return a support vector of the symmetric interval hull of a set in a given direction.

### Input

  * `d`   – direction
  * `sih` – symmetric interval hull of a set

### Output

A support vector of the symmetric interval hull of a set in the given direction. If the direction has norm zero, the origin is returned.

### Algorithm

For each non-zero entry in `d` we need to either look up the bound (if it has been computed before) or compute it, in which case we store it for future queries.
