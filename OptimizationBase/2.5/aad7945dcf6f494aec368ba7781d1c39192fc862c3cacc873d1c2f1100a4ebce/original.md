```
AutoFiniteDiff{T1,T2,T3} <: AbstractADType
```

An AbstractADType choice for use in OptimizationFunction for automatically generating the unspecified derivative functions. Usage:

```julia
OptimizationFunction(f, AutoFiniteDiff(); kwargs...)
```

This uses [FiniteDiff.jl](https://github.com/JuliaDiff/FiniteDiff.jl). While not necessarily the most efficient, this is the only choice that doesn't require the `f` function to be automatically differentiable, which means it applies to any choice. However, because it's using finite differencing, one needs to be careful as this procedure introduces numerical error into the derivative estimates.

  * Compatible with GPUs
  * Compatible with Hessian-based optimization
  * Compatible with Hv-based optimization
  * Compatible with constraint functions

Note that only the unspecified derivative functions are defined. For example, if a `hess` function is supplied to the `OptimizationFunction`, then the Hessian is not defined via FiniteDiff.

## Constructor

```julia
AutoFiniteDiff(; fdtype = Val(:forward)fdjtype = fdtype, fdhtype = Val(:hcentral))
```

  * `fdtype`: the method used for defining the gradient
  * `fdjtype`: the method used for defining the Jacobian of constraints.
  * `fdhtype`: the method used for defining the Hessian

For more information on the derivative type specifiers, see the [FiniteDiff.jl documentation](https://github.com/JuliaDiff/FiniteDiff.jl).
