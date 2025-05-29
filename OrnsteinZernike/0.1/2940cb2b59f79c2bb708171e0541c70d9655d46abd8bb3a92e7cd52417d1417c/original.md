```
DensityRamp <: Method
```

Solves the system by iteratively solving systems of increasing density, using the previous solution as initial guess at a higher density. This may help deal with convergence issues.

Arguments

  * `method`: method by which to solve the system for individual densities.
  * `densities`: densities to consider. Must be a vector of increasing values.
  * `verbose`: whether to print information.

Example: `DensityRamp(NgIteration(), [0.1, 0.3, 0.4]; verbose=false)`
