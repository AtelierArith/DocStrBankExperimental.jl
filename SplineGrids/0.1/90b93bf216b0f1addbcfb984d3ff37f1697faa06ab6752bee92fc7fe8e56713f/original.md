```
error_informed_local_refinement!(
    spline_grid::AbstractSplineGrid{Nin, Nout, HasWeights, Tv, Ti},
    error::AbstractArray;
    threshold_factor::Number = 1.0
    )::Nothing where {Nin, Nout, HasWeights, Tv, Ti}
```

Refine the last level of the locally refined spline grid informed by the `error` array which has the same shape as `spline_grid.eval`. This is done by:

  * mapping the error back onto the control points by using the adjoint of the refinement matrices multiplication
  * summing over the output dimensions to obtain a single number per control point stored in `control_grid_error`
  * activating each control point whose value is bigger than `threshold = threshold_factor * mean(control_grid_error)`
