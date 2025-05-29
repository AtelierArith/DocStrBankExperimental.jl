```
refine(
    spline_grid::A,
    dim_refinement::Integer;
    knots_new::Union{AbstractVector{<:AbstractFloat}, Nothing} = nothing)::Tuple{A, RefinementMatrix} where {A <: AbstractSplineGrid}
```

Create a new spline grid where multiple knots are added to the knot vector underlying the indicated spline dimension.

## Inputs

  * `spline_grid`: The spline grid from which one of the knot vectors will be refined
  * `dim_refinement`: The index of the spline dimension whose knot vector will be refined
  * `knots_new`: The knots that will be added. Defaults to `nothing`, which internally is translated to all midpoints of the non-trivial knot spans of the knot vector that will be refined.

## Outputs

  * `spline_grid_new`: The newly created spline grid with all the same underlying memory except for the updated knot vector and the control points.
  * `refinement_matrix`: The sparse matrix which expresses the basis functions from before the knot insertion in terms of the basis functions after the knot insertion for the knot insertion dimension.
