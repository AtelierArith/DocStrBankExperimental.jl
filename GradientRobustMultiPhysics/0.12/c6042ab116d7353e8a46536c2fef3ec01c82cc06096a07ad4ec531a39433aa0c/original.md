```
function L2BestapproximationProblem(
    uexact::AbstractUserDataType;
    bonus_quadorder::Int = 0,
    bestapprox_boundary_regions = [])
```

Creates an PDEDescription for an L2-Bestapproximation problem for the given exact function. Since this prototype already includes boundary and right-hand side data also a bonus quadrature order can be specified to steer the accuracy.
