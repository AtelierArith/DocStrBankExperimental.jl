```
interpolate_nans(grid, x, intp::Linear, extr::BoundaryCondition)
```

Interpolate `x` (which potentially has `NaN` values) linearly over the  provided `grid`.

If there are `NaN`s at the edges of `x`, then the `extrapolation_bc`  boundary condition is applied (see `Interpolations.BoundaryCondition` documentation for more details). The boundary condition defaults to `NaN`, which leaves the `NaN` values at the edges of `x` non-interpolated. Other boundary conditions, like `Flat(gt)` or `Line(gt)`, with  `gt = OnCell()` or `gt = OnGrid()` will also work.
