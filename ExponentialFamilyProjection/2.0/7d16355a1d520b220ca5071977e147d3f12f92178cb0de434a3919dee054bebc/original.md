```
ProjectionParameters(; kwargs...)
```

A type to hold the parameters for the projection procedure.  The following parameters are available:

  * `strategy = ExponentialFamilyProjection.DefaultStrategy()`: The strategy to use to compute the gradients.
  * `niterations = 100`: The number of iterations for the optimization procedure.
  * `tolerance = 1e-6`: The tolerance for the norm of the gradient.
  * `stepsize = ConstantLength(0.1)`: The stepsize for the optimization procedure. Accepts stepsizes from `Manopt.jl`.
  * `seed`: Optional; Seed for the `rng`
  * `rng`: Optional; Random number generator
  * `direction = BoundedNormUpdateRule(static(1.0)`: Direction update rule. Accepts `Manopt.DirectionUpdateRule` from `Manopt.jl`.
