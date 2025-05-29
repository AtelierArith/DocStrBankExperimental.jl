```
constraints_list(rm::ResetMap)
```

Return a list of constraints of a polyhedral reset map.

### Input

  * `rm` – reset map of a polyhedron

### Output

A list of constraints of the reset map.

### Notes

We assume that the underlying set `rm.X` is a polyhedron, i.e., offers a method `constraints_list(X)`.

### Algorithm

If the set `rm.X` is hyperrectangular, we iterate through all dimensions. For each reset we construct the corresponding (flat) constraints, and in the other dimensions we construct the corresponding constraints of the underlying set.

For more general sets, we fall back to `constraints_list` of a `LinearMap` of the `A`-matrix in the affine-map view of a reset map. Each reset dimension $i$ is projected to zero, expressed by two constraints for each reset dimension. Then it remains to shift these constraints to the new value.

For instance, if the dimension $5$ was reset to $4$, then there will be constraints $x₅ ≤ 0$ and $-x₅ ≤ 0$. We then modify the right-hand side of these constraints to $x₅ ≤ 4$ and $-x₅ ≤ -4$, respectively.
