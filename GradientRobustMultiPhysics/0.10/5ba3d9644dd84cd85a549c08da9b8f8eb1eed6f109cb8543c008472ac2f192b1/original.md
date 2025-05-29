```
function H1BestapproximationProblem(
    exact_function_gradient::AbstractUserDataType,
    exact_function_boundary::AbstractUserDataType;
    bonus_quadorder::Int = 0,
    bonus_quadorder_boundary::Int = 0,
    bestapprox_boundary_regions = [])
```

Creates an PDEDescription for an H1-Bestapproximation problem for the given exact function (only used on the boundary) and its exact gradient (used in the right-hand side). Since this prototype already includes boundary and right-hand side data also a bonus quadrature order can be specified to steer the accuracy.
