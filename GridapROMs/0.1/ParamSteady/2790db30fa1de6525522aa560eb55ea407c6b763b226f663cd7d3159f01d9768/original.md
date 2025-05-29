```
abstract type ParamFEOperator{O<:UnEvalOperatorType,T<:TriangulationStyle} <: FEOperator end
```

Parametric extension of a `FEOperator` in [`Gridap`](@ref). Compared to a standard FEOperator, there are the following novelties:

  * a ParamSpace is provided, so that parametric realizations can be extracted directly from the ParamFEOperator
  * a function representing a norm matrix is provided, so that errors in the desired norm can be automatically computed

Subtypes:

  * [`ParamFEOpFromWeakForm`](@ref)
  * [`LinearNonlinearParamFEOperator`](@ref)
  * [`TransientParamFEOperator`](@ref)
