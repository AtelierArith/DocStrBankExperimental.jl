```
SplineDimension(
    degree, 
    max_derivative_order, 
    knot_vector, 
    sample_points, 
    sample_indices, 
    eval, 
    eval_prev)
```

Defines the set of basis functions for a single dimension, and how it is sampled.

## Arguments

  * `degree`: The degree of the piecewise polynomial basis functions.
  * `max_derivative_order`: The maximum derivative order of the basis functions that will be computed.
  * `knot_vector`: The knot vector on which the basis functions are defined.
  * `sample_points`: The points in the domain of the basis functions where they are sampled. Must
  * lie within the boundaries of the knot vector.
  * `sample_indices`: The indices `i` of the sample points `t` in the knot vector such that `knot_vector.knots[i] ≤ t < knot_vector.knots[i + 1]``
  * `eval`: An array of shape `(length(sample_points), degree + 1, max_derivative + 1)`, with per sample point the values of those basis functions
  * `eval_prev`: Helper array for intermediate results in the basis function computations whose support the sample point is in, and the derivatives if requested.
