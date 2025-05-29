```
evaluate!(spline_grid::SplineGrid{Nin};
    derivative_order::NTuple{Nin, <:Integer} = ntuple(_ -> 0, Nin),
    control_points::AbstractArray = spline_grid.control_points,
    eval::AbstractArray = spline_grid.eval)
```

Evaluate the spline grid, that is: take the evaluated basis functions for each sample point for each SplineDimension, and compute the output grid on each sample point combination as a linear combination of control points with basis function products as coefficients.

If weights are supplied, compute the rational basis functions for NURBS as the control point coefficients.

Uses the `control_points` and `eval` arrays from the `spline_grid` by default, but different arrays can be specified as a convenience for optimization algorithms.
