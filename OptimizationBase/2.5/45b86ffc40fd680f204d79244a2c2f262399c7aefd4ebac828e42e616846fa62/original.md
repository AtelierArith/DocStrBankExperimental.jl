```
AutoZygote <: AbstractADType
```

An AbstractADType choice for use in OptimizationFunction for automatically generating the unspecified derivative functions. Usage:

```julia
OptimizationFunction(f, AutoZygote(); kwargs...)
```

This uses the [Zygote.jl](https://github.com/FluxML/Zygote.jl) package. This is the staple reverse-mode AD that handles a large portion of Julia with good efficiency. Hessian construction is fast via forward-over-reverse mixing ForwardDiff.jl with Zygote.jl

  * Compatible with GPUs
  * Compatible with Hessian-based optimization via ForwardDiff
  * Compatible with Hv-based optimization via ForwardDiff
  * Not compatible with constraint functions

Note that only the unspecified derivative functions are defined. For example, if a `hess` function is supplied to the `OptimizationFunction`, then the Hessian is not defined via Zygote.
