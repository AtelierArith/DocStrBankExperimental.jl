```
insert_knot(
    spline_grid::A,
    dim_refinement::Integer,
    knot_new::AbstractFloat;
    evaluate_spline_dimension::Bool = true)::Tuple{A, RefinementMatrix} where {A <: AbstractSplineGrid}
```

Create a new spline grid where a new knot is added to the knot vector underlying the indicated spline dimension.

## Inputs

  * `spline_grid`: The spline grid to which the new knot will be added
  * `knot_new`: The value of the knot to be added
  * `dim_refinement`: The index of the spline dimension to which the knot will be added
  * `evaluate_spline_dimension`: Whether the spline dimension to which the knot is added should be evaluated. Defaults to `true`.

## Outputs

  * `spline_grid_new`: The newly created spline grid with all the same underlying memory except for the updated knot vector and the control points.
  * `refinement_matrix`: The sparse matrix which expresses the basis functions from before the knot insertion in terms of the basis functions after the knot insertion for the knot insertion dimension.
