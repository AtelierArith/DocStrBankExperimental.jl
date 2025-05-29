```
etp = linear_interpolation(knots, A; extrapolation_bc=Throw())
```

A shorthand for one of the following.

  * `extrapolate(scale(interpolate(A, BSpline(Linear())), knots), extrapolation_bc)`
  * `extrapolate(interpolate(knots, A, Gridded(Linear())), extrapolation_bc)`,

depending on whether `knots` are ranges or vectors.

Consider using `interpolate`, `scale`, or `extrapolate` explicitly as needed rather than using this convenience constructor. Performance will improve without scaling or extrapolation.
