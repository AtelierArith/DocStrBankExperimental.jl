```
refine(
    spline_grid::AbstractSplineGrid{Nin, Nout, false, Tv, Ti},
    spline_dimension_new::SplineDimension{Tv, Ti},
    dim_refinement::Integer,
    refinement_matrix::RefinementMatrix{Tv, Ti} where {Nin, Nout, Tv, Ti}
```

Update the spline grid with a refined spline dimension in the specified dimension with the associated refinement matrix.
