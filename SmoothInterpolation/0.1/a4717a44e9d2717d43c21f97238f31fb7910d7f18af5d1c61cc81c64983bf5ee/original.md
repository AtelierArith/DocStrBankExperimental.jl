```
SmoothedLinearInterpolation(u, t; λ = 0.25, extrapolate = false)
```

The method of interpolating between the data points using a linear polynomial, with an anterval around the corner points being replaced by a smooth spline section.

## Arguments

  * `u`: data points.
  * `t`: time points.

## Keyword Arguments

  * `extrapolate`: boolean value to allow extrapolation. Defaults to `false`.
  * `λ`: The relative size of the spline interval. The interval extents a fraction `λ/2` towards the neighbouring time points.
