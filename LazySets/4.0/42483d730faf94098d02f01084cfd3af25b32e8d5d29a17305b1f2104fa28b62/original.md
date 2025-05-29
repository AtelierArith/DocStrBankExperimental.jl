```
linear_map(M::AbstractMatrix, cp::CartesianProduct)
```

Concrete linear map of a (polyhedral) Cartesian product.

### Input

  * `M`  – matrix
  * `cp` – Cartesian product

### Output

A polytope if `cp` is bounded and a polyhedron otherwise.

### Algorithm

We convert the Cartesian product to constraint representation and then call `linear_map` on the corresponding polyhedron.

This is a fallback implementation and will fail if the wrapped sets are not polyhedral.
