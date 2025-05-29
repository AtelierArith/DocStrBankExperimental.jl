```
lcurve(lower, upper ; kwargs...)
```

Constructor for finding the optimal alpha value via lcurve curvature univariate optimization, given some lower and upper bounds.

Necessary (positional) arguments:

  * `lower` is the lower bound, or lowest alpha value the algorighm will consider.
  * `upper` is the upper bound, or highest alpha value the algorighm will consider.

Optional (keyword) arguments:

  * `algorithm` determines which method will be used by Optim.jl to solve the problem.

Default is `Brent()` and the only alternative is `GoldenSection()`, which is normally slower.

  * `abs_tol` determines what's the smallest change in alpha the algorithm should care about.

Default is 1e-3.
