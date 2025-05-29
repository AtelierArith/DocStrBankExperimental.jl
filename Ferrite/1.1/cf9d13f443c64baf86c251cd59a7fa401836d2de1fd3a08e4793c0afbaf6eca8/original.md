```
spatial_coordinate(fe_v::AbstractValues, q_point::Int, x::AbstractVector)
```

Compute the spatial coordinate in a quadrature point. `x` contains the nodal coordinates of the cell.

The coordinate is computed, using the geometric interpolation, as $\mathbf{x} = \sum\limits_{i = 1}^n M_i (\mathbf{\xi}) \mathbf{\hat{x}}_i$.

where $\xi$is the coordinate of the given quadrature point `q_point` of the associated quadrature rule.
