```
SplineInterpolation
```

Spline interpolation.

This is the type returned by [`interpolate`](@ref).

A `SplineInterpolation` `I` can be evaluated at any point `x` using the `I(x)` syntax.

It can also be updated with new data on the same data points using [`interpolate!`](@ref).

---

```
SplineInterpolation(undef, B::AbstractBSplineBasis, x::AbstractVector, [T = eltype(x)])
```

Initialise a `SplineInterpolation` from B-spline basis and a set of interpolation (or collocation) points `x`.

Note that the length of `x` must be equal to the number of B-splines.

Use [`interpolate!`](@ref) to actually interpolate data known on the `x` locations.
