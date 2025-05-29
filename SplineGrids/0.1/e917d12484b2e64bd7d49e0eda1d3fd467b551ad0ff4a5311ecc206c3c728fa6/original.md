```
insert_knot(
    spline_dimension::SplineDimension{Tv, Ti},
    knot_new::AbstractFloat;
    recompute_sample_indices::Bool = true,
    evaluate::Bool = true)::Tuple{
        SplineDimension{Tv, Ti},
        RefinementMatrix{Tv, Ti}
    } where {Tv, Ti}
```

Create a new spline dimension whose knot vector has the new knot with multiplicity 1.

## Inputs

  * `spline_dimension`: The spline dimension the new knot will be added to
  * `knot_new`: The value of the new knot
  * `recompute_sample_indices`: Whether the indices of the sample points should be recomputed after the knot insertion. Defaults to `true`.
  * `evaluate`: Whether the spline dimension should be evaluated after the knot insertion. Defaults to `true`.

## Outputs

  * `spline_dimension_new`: The newly created spline dimension with the same underlying memory except for the new knot vector.
  * `refinement_matrix`: The sparse matrix which expresses the basis functions from before the knot insertion in terms of the basis functions after the knot insertion.
