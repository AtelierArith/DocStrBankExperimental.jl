```
jacobian_matrix(mesh, CI::CartesianIndex)
```

Get the Jacobian matrix of the forward transformation (ξ,η,ζ) → (x,y,z). Use `inv(jacobian_matrix(mesh, idx))` to get the inverse transformation (∂ξ/∂x, ∂ξ/∂y, ...). Note, finding the inverse metrics this way will not be conservative, e.g. observe the geometric conservation law.
