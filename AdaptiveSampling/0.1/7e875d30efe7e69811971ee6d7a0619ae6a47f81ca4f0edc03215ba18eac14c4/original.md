```
sample_costs(f, a, b; cost::AbstractCost=CompositeCost((UniformCost(a, b), VisvalingamCost(a, b, f(a), f(b))), (1, 100)), tol=1e-3, maxsamples=10000)
```

Samples the function `f` over the interval `[a, b]` and computes the associated costs using the specified cost function. The sampling process continues until the maximum cost is below the tolerance `tol` or the maximum number of samples `maxsamples` is reached.

# Arguments

  * `f`: The function to be sampled.
  * `a`: The start of the interval.
  * `b`: The end of the interval.
  * `cost::AbstractCost`: The cost function to be used. Defaults to a composite cost combining `UniformCost` and `VisvalingamCost`.
  * `tol`: The tolerance for the maximum cost. Defaults to `1e-3`.
  * `maxsamples`: The maximum number of samples. Defaults to `10000`.

# Returns

  * `x`: A vector of sample points.
  * `y`: A vector of function values at the sample points.
  * `c`: A vector of costs associated with the sample points.
