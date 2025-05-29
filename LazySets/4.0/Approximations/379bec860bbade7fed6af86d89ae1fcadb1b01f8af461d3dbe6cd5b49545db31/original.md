```
box_approximation(S::CartesianProductArray{N, <:AbstractHyperrectangle}) where {N}
```

Overapproximate the Cartesian product of a finite number of hyperrectangular sets by a tight hyperrectangle.

### Input

  * `S`– Cartesian product of a finite number of hyperrectangular sets

### Output

A hyperrectangle.

### Algorithm

This method falls back to the `convert` method. Since the sets wrapped by the Cartesian product array are hyperrectangles, this can be done without overapproximation.
