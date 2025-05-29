```
polybspline(controlpoints::Vector{Point}, npoints; degree=3, clamped=true)
```

Generate a B-spline curve from a given set of control points.

# Arguments

  * `controlpoints::Vector{Point}`: An array of control points that define the B-spline.
  * `npoints=100`: The number of points to generate on the B-spline curve.
  * `degree=3`: The degree of the B-spline. Default is 3.
  * `clamped=true`: A boolean to indicate if the B-spline is clamped. Default is true.

# Returns

  * An array of points on the B-spline curve.
