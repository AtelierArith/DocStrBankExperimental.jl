```
points_linear(f, domain, tol::T; scan_step = (domain[end] - domain[begin]) / 100) where T <: Real
```

Computes points used for a linear interpolation of the function `f` in the given `domain` within a tolerance `tol`.

See also [`points_linear_singular`](@ref) for managing singular points.

# Arguments

  * `f`: The function used for the linear interpolation. It must be of the form of f(x), where `x` is a number.
  * `domain`: a tuple or array representing the interpolation domain, e.g., the tuple (a, b).
  * `tol::T where T <: Real`: the desired tolerance of the points. The real value of the function at any point xᵢ minus the aproximation will be smaller than `tol`, i.e., |f(xᵢ) - yᵢ| < tol.

# Keywords

  * `scan_step`: Minimum step size that will be used to scan the whole domain. The returned points will have at least a spacing of `scan_step`. Very small values will produce a very long execution time. By default it will divide the domain in 100 intervals.

# Returns

  * `(xs, ys)`: A tuple containing two arrays of points, `xs` for the independent variable and `ys` for the computed values of the function.

# Notes

The function `f` must have a continuous second derivative in order to compute the linear interpolation error. This second derivative is computed using `Enzyme`'s automatic differentiation.

If the returned `(xs, ys)` contains just the endpoints, try decreasing the `scan_step` size and/or increasing the tolerance `tol`.

If the execution time of a single call to the function `f` is quite long, this adaptive method might not be suitable.
