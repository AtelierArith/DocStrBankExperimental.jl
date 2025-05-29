```
kde = KDEDist(data)
```

A univariate distribution that obeys the Distributions.jl interface. Uses KernelDensity.jl to create a 1D kernel density estimator using the provided input data and optional bandwidth scale factor.

Appropriate to use as a prior in an Octofitter model.
