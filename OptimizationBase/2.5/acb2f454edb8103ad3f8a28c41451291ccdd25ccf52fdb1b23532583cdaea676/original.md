```
AutoModelingToolkit <: AbstractADType
```

An AbstractADType choice for use in OptimizationFunction for automatically generating the unspecified derivative functions. Usage:

```julia
OptimizationFunction(f, AutoModelingToolkit(); kwargs...)
```

This uses the [ModelingToolkit.jl](https://github.com/SciML/ModelingToolkit.jl) package's `modelingtookitize` functionality to generate the derivatives and other fields of an `OptimizationFunction`. This backend creates the symbolic expressions for the objective and its derivatives as well as the constraints and their derivatives. Through `structural_simplify`, it enforces simplifications that can reduce the number of operations needed to compute the derivatives of the constraints. This automatically generates the expression graphs that some solver interfaces through OptimizationMOI like [AmplNLWriter.jl](https://github.com/jump-dev/AmplNLWriter.jl) require.

  * Compatible with GPUs
  * Compatible with Hessian-based optimization
  * Compatible with Hv-based optimization
  * Compatible with constraints

Note that only the unspecified derivative functions are defined. For example, if a `hess` function is supplied to the `OptimizationFunction`, then the Hessian is not generated via ModelingToolkit.

## Constructor

```julia
AutoModelingToolkit(false, false)
```

  * `obj_sparse`: to indicate whether the objective hessian is sparse.
  * `cons_sparse`: to indicate whether the constraints' jacobian and hessian are sparse.
