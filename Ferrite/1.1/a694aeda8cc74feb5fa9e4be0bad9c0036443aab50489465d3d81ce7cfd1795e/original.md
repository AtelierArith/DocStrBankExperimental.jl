```
spatial_coordinate(ip::ScalarInterpolation, ξ::Vec, x::AbstractVector{<:Vec{sdim, T}})
```

Compute the spatial coordinate in a given quadrature point. `x` contains the nodal coordinates of the cell.

The coordinate is computed, using the geometric interpolation, as $\mathbf{x} = \sum\limits_{i = 1}^n M_i (\mathbf{\xi}) \mathbf{\hat{x}}_i$
