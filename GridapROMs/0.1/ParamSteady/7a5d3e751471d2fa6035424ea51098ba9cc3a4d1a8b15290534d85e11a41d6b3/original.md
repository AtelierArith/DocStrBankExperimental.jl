```
struct LinearNonlinearParamFEOperator{O<:UnEvalOperatorType,T<:TriangulationStyle} <: ParamFEOperator{O,T}
  op_linear::ParamFEOperator
  op_nonlinear::ParamFEOperator
end
```

Interface to accommodate the separation of terms depending on their linearity in a nonlinear problem. This allows to build and store once and for all linear residuals/Jacobians, and in the Newton-like iterations only evaluate and assemble only the nonlinear components
