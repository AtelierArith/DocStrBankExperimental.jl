```
abstract type OperatorTriple{<:AbstractFunctionOperator,<:AbstractFunctionOperator} <: AbstractFunctionOperator
```

allows to evaluate three operators in place of one, e.g. OperatorTriple{Identity,Gradient,Hessian}.
