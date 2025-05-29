```
overapproximate(rm::ResetMap{N, <:CartesianProductArray},
                ::Type{<:CartesianProductArray}, oa) where {N}
```

Overapproximate a reset map (that only resets to zero) of a Cartesian product with a new Cartesian product.

### Input

  * `rm`                    – reset map
  * `CartesianProductArray` – target set type
  * `oa`                    – overapproximation option

### Output

A Cartesian product with the same block structure.

### Notes

This implementation currently only supports resets to zero.

### Algorithm

We convert the `ResetMap` into a `LinearMap` and then call the corresponding `overapproximate` method.
