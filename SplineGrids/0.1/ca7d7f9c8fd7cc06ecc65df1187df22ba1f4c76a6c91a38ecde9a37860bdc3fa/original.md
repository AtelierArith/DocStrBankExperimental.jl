```
insert_knot(
knot_vector::KnotVector, 
knot_new::AbstractFloat)::Tuple{KnotVector, Integer}
```

Create a new knot vector with the new knot of multiplicity 1.

## Inputs

  * `knot_vector`: The knot vector object to which the knot will be added
  * `knot_new`: The value of the new knot. Should not be part of the knot values already

## Outputs

  * `knot_vector_new`: The newly created knot vector with the added knot
  * `knot_span_index`: The index such that `knots_all[knot_span_index] ≤ knot_new < knots_all[knot_span_index + 1]`
