```
abstract type OperatorTriple{<:StandardFunctionOperator,<:StandardFunctionOperator} <: StandardFunctionOperator
```

は、1つの代わりに3つの演算子を評価することを可能にします。例えば、OperatorTriple{Identity,Gradient,Hessian}です。
