```
etp = constant_interpolation(knots, A; extrapolation_bc=Throw())
```

A shorthand for `extrapolate(interpolate(knots, A, scheme), extrapolation_bc)`, where `scheme` is either `BSpline(Constant())` or `Gridded(Constant())` depending on whether `knots` are ranges or vectors.

Consider using `interpolate` or `extrapolate` explicitly as needed rather than using this convenience constructor. Performance will improve without extrapolation.
