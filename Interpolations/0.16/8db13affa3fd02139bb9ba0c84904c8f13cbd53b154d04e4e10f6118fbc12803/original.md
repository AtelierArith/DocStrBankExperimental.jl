```
etp = cubic_spline_interpolation(knots, A; bc=Line(OnGrid()), extrapolation_bc=Throw())
```

A shorthand for `extrapolate(scale(interpolate(A, BSpline(Cubic(bc))), knots), extrapolation_bc)`.

Consider using `interpolate`, `scale`, or `extrapolate` explicitly as needed rather than using this convenience constructor. Performance will improve without scaling or extrapolation.
