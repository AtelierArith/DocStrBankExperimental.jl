```
BSpline{S,T}()
```

yields a B-spline (short for *basis spline*) of order `S` that is a piecewise polynomial function of degree `S - 1` on a support of length `S`.  The parameter `T` is the floating-point type for computations, `T = Float64` is assuled if this parameter is not specified.

Fr now, not all B-spline are implemented in `InterpolationKernels`, `S` must be: `1` (for a **rectangular** B-spline), `2` (for a **linear** B-spline), `3` (for a **quadratic** B-spline), or `4` (for a **cubic** B-spline).

If `ker` is a B-spline, then `ker'` is its derivative which can also be directly constructed by calling [`BSplinePrime`](@ref).

!!! warning
    The derivative of B-splines of order `S ≤ 2` is not defined everywhere.  It is allowed to take their derivative but it (arbitrarily) yields zero where not defined.  Returning `NaN` would have been more correct but it has been considered that it would do more harm than good in practice.

