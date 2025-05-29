```
get_2d_interpolator(xs, ys, fs; method = BilinearInterpolant, cap_endpoints = true)
```

For `xs` of length `nx` and `ys` of length `ny` generate a 2D interpolation for values given as a `nx` by `ny` matrix. By default `cap_endpoints=true`, and constant extrapolation is used. Fine-grined control over extrapolation can be achieved by setting the keywords arguments `cap_x = (cap_low_x, cap_high_x)` and analogously for `cap_y`.
