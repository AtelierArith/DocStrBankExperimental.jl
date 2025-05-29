```
const TransientParamFEOperator{O<:ODEParamOperatorType,T<:TriangulationStyle} = ParamFEOperator{O,T}
```

Parametric extension of a `TransientFEOperator` in [`Gridap`](@ref). Compared to a standard TransientFEOperator, there are the following novelties:

  * a [`TransientParamSpace`](@ref) is provided, so that parametric realizations can be extracted directly from the `TransientParamFEOperator`
  * a function representing a norm matrix is provided, so that errors in the desired norm can be automatically computed

Subtypes:

  * [`TransientParamFEOpFromWeakForm`](@ref)
  * [`TransientParamLinearFEOpFromWeakForm`](@ref)
