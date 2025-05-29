```
mass_matrix_boundary(D::AbstractDerivativeOperator)
```

Construct the mass matrix at the boundary of a derivative operator `D`. For classical 1D non-periodic operators, this is the matrix `Diagonal([-1, 0, ..., 0, 1])`. For periodic 1D operators this is the zero matrix.
