```
RefinementMatrix(
    spline_dimension::SplineDimension{Tv, Ti},
    knot_span_index::Integer,
    knot_new
    )::RefinementMatrix{Tv, Ti} where {Tv, Ti <: Integer}
```

Build a refinement matrix per row given a knot vector and a to be added new knot.

## Inputs

  * `spline_dimension`: The spline dimension whose knot vector the new knot is to be added to
  * `knot_span_index`: The index such that `knots_all[knot_span_index] ≤ knot_new < knots_all[knot_span_index + 1]`
  * `knot_new`: The value of the new knot
