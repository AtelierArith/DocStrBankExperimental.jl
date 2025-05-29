```
AutoEnzyme <: AbstractADType
```

An AbstractADType choice for use in OptimizationFunction for automatically generating the unspecified derivative functions. Usage:

```julia
OptimizationFunction(f, AutoEnzyme(); kwargs...)
```

This uses the [Enzyme.jl](https://github.com/EnzymeAD/Enzyme.jl) package. Enzyme performs automatic differentiation on the LLVM IR code generated from julia. It is highly-efficient and its ability perform AD on optimized code allows Enzyme to meet or exceed the performance of state-of-the-art AD tools.

  * Compatible with GPUs
  * Compatible with Hessian-based optimization
  * Compatible with Hv-based optimization
  * Compatible with constraints

Note that only the unspecified derivative functions are defined. For example, if a `hess` function is supplied to the `OptimizationFunction`, then the Hessian is not defined via Enzyme.
