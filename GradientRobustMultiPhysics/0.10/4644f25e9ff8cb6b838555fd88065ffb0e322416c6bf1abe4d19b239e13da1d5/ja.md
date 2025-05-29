```
abstract type OperatorTriple{<:AbstractFunctionOperator,<:AbstractFunctionOperator} <: AbstractFunctionOperator
```

は、1つの代わりに3つのオペレーターを評価することを可能にします。例えば、OperatorTriple{Identity,Gradient,Hessian}です。
