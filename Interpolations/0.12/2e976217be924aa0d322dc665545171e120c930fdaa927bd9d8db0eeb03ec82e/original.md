```
itp = interpolate(A, interpmode)
```

Interpolate an array `A` in the mode determined by `interpmode`. `interpmode` may be one of

  * `NoInterp()`
  * `BSpline(Constant())`
  * `BSpline(Linear())`
  * `BSpline(Quadratic(bc))` (see [`BoundaryCondition`](@ref))
  * `BSpline(Cubic(bc))`

It may also be a tuple of such values, if you want to use different interpolation schemes along each axis.
