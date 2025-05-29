```
ρ(d::AbstractVector, cpa::CartesianProductArray)
```

Evaluate the support function of a Cartesian product of a finite number of sets.

### Input

  * `d`   – direction
  * `cpa` – Cartesian product of a finite number of sets

### Output

The evaluation of the support function in the given direction. If the direction has norm zero, the result depends on the wrapped sets.
