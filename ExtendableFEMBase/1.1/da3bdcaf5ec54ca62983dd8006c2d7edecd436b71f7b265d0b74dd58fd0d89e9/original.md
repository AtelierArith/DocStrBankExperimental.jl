```
abstract type OperatorPair{<:StandardFunctionOperator,<:StandardFunctionOperator} <: StandardFunctionOperator
```

allows to evaluate two operators in place of one, e.g. OperatorPair{Identity,Gradient}.
