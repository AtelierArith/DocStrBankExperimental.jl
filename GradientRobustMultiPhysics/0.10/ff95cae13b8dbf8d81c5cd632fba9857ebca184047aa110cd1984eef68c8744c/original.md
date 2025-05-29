```
abstract type OperatorPair{<:AbstractFunctionOperator,<:AbstractFunctionOperator} <: AbstractFunctionOperator
```

allows to evaluate two operators in place of one, e.g. OperatorPair{Identity,Gradient}.
