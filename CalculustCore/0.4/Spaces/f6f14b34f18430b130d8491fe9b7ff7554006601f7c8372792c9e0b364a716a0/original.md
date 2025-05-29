```
gradientOp(V::AbstractSpace{T, D}) where{T, D} -> [∂x1, ..., ∂xD]
```

Gradient Operator: ∇

Returns a size `D` `Vector` of operators. The `d`th operator corresponds to the linear transformation from a function to its partial derivative in the `d`th dimension at the grid points of `V`. Its `[ij]`th entry is equal to the  value of the derivative of the `j`th basis function at the `i`th grid point.

$[D]_{ij} = \partial_{x}\phi_{j}(x_i)$
