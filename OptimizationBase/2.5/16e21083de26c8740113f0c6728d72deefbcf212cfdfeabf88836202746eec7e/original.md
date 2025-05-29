```
AutoReverseDiff <: AbstractADType
```

An AbstractADType choice for use in OptimizationFunction for automatically generating the unspecified derivative functions. Usage:

```julia
OptimizationFunction(f, AutoReverseDiff(); kwargs...)
```

This uses the [ReverseDiff.jl](https://github.com/JuliaDiff/ReverseDiff.jl) package. `AutoReverseDiff` has a default argument, `compile`, which denotes whether the reverse pass should be compiled. **`compile` should only be set to `true` if `f` contains no branches (if statements, while loops) otherwise it can produce incorrect derivatives!**

`AutoReverseDiff` is generally applicable to many pure Julia codes, and with `compile=true` it is one of the fastest options on code with heavy scalar interactions. Hessian calculations are fast by mixing ForwardDiff with ReverseDiff for forward-over-reverse. However, its performance can falter when `compile=false`.

  * Not compatible with GPUs
  * Compatible with Hessian-based optimization by mixing with ForwardDiff
  * Compatible with Hv-based optimization by mixing with ForwardDiff
  * Not compatible with constraint functions

Note that only the unspecified derivative functions are defined. For example, if a `hess` function is supplied to the `OptimizationFunction`, then the Hessian is not defined via ReverseDiff.

## Constructor

```julia
AutoReverseDiff(; compile = false)
```

#### Note: currently, compilation is not defined/used!
