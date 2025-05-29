```
itp = interpolate(A, interpmode, gridstyle, λ, k)
```

Interpolate an array `A` in the mode determined by `interpmode` and `gridstyle` with regularization following [1], of order `k` and constant `λ`.  `interpmode` may be one of

  * `BSpline(NoInterp())`
  * `BSpline(Linear())`
  * `BSpline(Quadratic(BC()))` (see [`BoundaryCondition`](@ref))
  * `BSpline(Cubic(BC()))`

It may also be a tuple of such values, if you want to use different interpolation schemes along each axis.

`gridstyle` should be one of `OnGrid()` or `OnCell()`.

`k` corresponds to the derivative to penalize. In the limit λ->∞, the interpolation function is a polynomial of order `k-1`. A value of 2 is the most common.

`λ` is non-negative. If its value is zero, it falls back to non-regularized interpolation.

[1] https://projecteuclid.org/euclid.ss/1038425655.
