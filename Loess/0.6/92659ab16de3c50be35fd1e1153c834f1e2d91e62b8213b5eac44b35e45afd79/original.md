```
loess(xs, ys; normalize=true, span=0.75, degree=2)
```

Fit a loess model.

Args:

  * `xs`: A `n` by `m` matrix with `n` observations from `m` independent predictors
  * `ys`: A length `n` response vector.
  * `normalize`: Normalize the scale of each predicitor. (default true when `m > 1`)
  * `span`: The degree of smoothing, typically in [0,1]. Smaller values result in smaller   local context in fitting.
  * `degree`: Polynomial degree.
  * `cell`: Control parameter for bucket size. Internal interpolation nodes will be added to the K-D tree until the number of bucket element is below `n * cell * span`.

Returns:   A fit `LoessModel`.
