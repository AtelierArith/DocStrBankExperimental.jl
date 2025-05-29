```
AutoTracker <: AbstractADType
```

An AbstractADType choice for use in OptimizationFunction for automatically generating the unspecified derivative functions. Usage:

```julia
OptimizationFunction(f, AutoTracker(); kwargs...)
```

This uses the [Tracker.jl](https://github.com/FluxML/Tracker.jl) package. Generally slower than ReverseDiff, it is generally applicable to many pure Julia codes.

  * Compatible with GPUs
  * Not compatible with Hessian-based optimization
  * Not compatible with Hv-based optimization
  * Not compatible with constraint functions

Note that only the unspecified derivative functions are defined. For example, if a `hess` function is supplied to the `OptimizationFunction`, then the Hessian is not defined via Tracker.
