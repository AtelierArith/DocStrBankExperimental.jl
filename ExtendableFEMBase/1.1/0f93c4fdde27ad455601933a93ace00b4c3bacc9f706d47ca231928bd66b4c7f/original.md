```
abstract type OperatorTriple{<:StandardFunctionOperator,<:StandardFunctionOperator} <: StandardFunctionOperator
```

allows to evaluate three operators in place of one, e.g. OperatorTriple{Identity,Gradient,Hessian}.
