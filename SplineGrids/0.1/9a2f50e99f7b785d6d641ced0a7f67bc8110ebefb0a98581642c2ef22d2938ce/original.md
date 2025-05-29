```
refine(
    spline_dimension::SplineDimension{Tv, Ti};
    knots_new::Union{Vector{<:AbstractFloat}, Nothing} = nothing)::Tuple{SplineDimension{Tv, Ti}, RefinementMatrix{Tv, Ti}} where {Tv, Ti}
```

Create a new spline dimension with multiple knots added to the underlying knot vector.

## Inputs

  * `spline_dimension`: The spline dimension the new knots will be added to
  * `knots_new`: The vector of knots that will be added. Defaults to the midpoints of the knot spans of the vector underlying the spline dimension.

## Outputs

  * `spline_dimension_new`: The newly created spline dimension with the same underlying memory except for the new knot vector.
  * `refinement_matrix`: The sparse matrix which expresses the basis functions from before the refinement in terms of the basis functions after the refinement.
