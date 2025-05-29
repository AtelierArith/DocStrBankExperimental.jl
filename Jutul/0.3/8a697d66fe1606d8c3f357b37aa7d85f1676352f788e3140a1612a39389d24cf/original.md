```
get_1d_interpolator(xs, ys; <keyword arguments>)
```

Get a 1D interpolator `F(x) ≈ y` for a table `xs, ys` that by default does constant extrapolation

# Arguments

  * `xs`: sorted list of parameter points.
  * `ys`: list of function values with equal length to `xs`
  * `method=LinearInterpolant`: constructor for the interpolation. Defaults to `LinearInterpolant` which does simple linear interpolation.
  * `cap_endpoints = true`: Add values so that the endpoints are capped (constant extrapolation). Otherwise, the extrapolation will match the method.
  * `cap_start = cap_endpoints`: Fine-grained version of cap_endpoints for the start of the interval only (extrapolation for `x < xs[1]`)
  * `cap_end = cap_endpoints`:Fine-grained version of cap_endpoints for the end of the interval only (extrapolation for `x > xs[end]`)

Additional keyword arguments are passed onto the interpolator constructor.
