```
interpolate(kp::KPath, N::Integer)
interpolate(kp::KPath; N::Integer, density::Real) --> KPathInterpolant
```

Return an interpolant of `kp` with `N` points distributed approximately equidistantly across the full **k**-path (equidistance is measured in a Cartesian metric).

Note that the interpolant may contain slightly fewer or more points than `N` (typically fewer) in order to improve equidistance. `N` can also be provided as a keyword argument.

As an alternative to specifying the desired total number of interpolate points via `N`, a desired density per unit (reciprocal) length can be specified via the keyword argument `density`.
