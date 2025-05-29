```
AutoForwardDiff{chunksize} <: AbstractADType
```

An AbstractADType choice for use in OptimizationFunction for automatically generating the unspecified derivative functions. Usage:

```julia
OptimizationFunction(f, AutoForwardDiff(); kwargs...)
```

This uses the [ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl) package. It is the fastest choice for small systems, especially with heavy scalar interactions. It is easy to use and compatible with most Julia functions which have loose type restrictions. However, because it's forward-mode, it scales poorly in comparison to other AD choices. Hessian construction is suboptimal as it uses the forward-over-forward approach.

  * Compatible with GPUs
  * Compatible with Hessian-based optimization
  * Compatible with Hv-based optimization
  * Compatible with constraints

Note that only the unspecified derivative functions are defined. For example, if a `hess` function is supplied to the `OptimizationFunction`, then the Hessian is not defined via ForwardDiff.
