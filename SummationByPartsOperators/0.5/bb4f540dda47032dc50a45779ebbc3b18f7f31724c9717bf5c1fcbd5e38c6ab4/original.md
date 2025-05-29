```
mass_matrix_boundary(D::AbstractMultidimensionalMatrixDerivativeOperator, dim)
```

Construct the mass matrix at the boundary of a [`MultidimensionalMatrixDerivativeOperator`](@ref) `D` in direction `dim`. The boundary mass matrix is constructed to be mimetic, see

  * Jan Glaubitz, Simon-Christian Klein, Jan Nordström, Philipp Öffner (2023) Multi-dimensional summation-by-parts operators for general function spaces: Theory and construction Journal of Computational Physics 491, 112370, [DOI: 10.1016/j.jcp.2023.112370](https://doi.org/10.1016/j.jcp.2023.112370).
