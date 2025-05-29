```
interpOp(V1::AbstractSpace, V2::AbstractSpace)
```

Grid to grid interpolation operator from `V1` to `V2`. Both spaces must share the same domain. Its `[ij]`th entry is the value of the `j`th basis function of `V1` at the `i`th grid point of `V2`.

$[J]_{ij} = \phi_{j}(x_i)$

If `V1 == V2`, we simply return the no-op `IdentityOperator(V1)`.
