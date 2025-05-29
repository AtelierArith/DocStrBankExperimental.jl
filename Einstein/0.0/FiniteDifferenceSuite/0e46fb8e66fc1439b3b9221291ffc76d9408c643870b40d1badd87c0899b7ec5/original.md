```
LocalBarycentricInterpolation(points, values; degree=4)
```

Construct a local barycentric Lagrange interpolant for equispaced data points.

Creates a polynomial approximation of degree `degree` using the data `values` at uniformly  spaced points `points`. The interpolation is performed locally using `degree + 1` points  nearest to the evaluation point.

# Arguments

  * `points::StepRangeLen{TF}`: Equispaced points for interpolation
  * `values::AbstractVector{TF}`: Function values at the points
  * `degree::Integer=4`: Degree of the local polynomial interpolant

# Returns

  * An interpolant function that can be evaluated at any point within `[minimum(points), maximum(points)]`

# Notes

  * Requires `length(points) >= degree + 1`
  * `points` and `values` must have the same length
  * Uses barycentric Lagrange interpolation for numerical stability

# References

  * [Berrut2004](@citet*)
