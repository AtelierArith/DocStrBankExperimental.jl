```
    intersection(X::CartesianProductArray, Y::CartesianProductArray)
```

Compute the intersection between Cartesian products of a finite number of sets with identical decomposition.

### Input

  * `X` – Cartesian product of a finite number of sets
  * `Y` – Cartesian product of a finite number of sets

### Output

The decomposed set that represents the concrete intersection of `X` and `Y`.

### Algorithm

This algorithm intersects the corresponding blocks of the sets.
