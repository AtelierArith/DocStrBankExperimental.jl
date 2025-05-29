```
σ(d::AbstractVector, cpa::CartesianProductArray)
```

Compute a support vector of a Cartesian product of a finite number of sets.

### Input

  * `d`   – direction
  * `cpa` – Cartesian product of a finite number of sets

### Output

A support vector in the given direction. If the direction has norm zero, the result depends on the product sets.
