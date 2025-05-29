```
abstract type OperatorPair{<:AbstractFunctionOperator,<:AbstractFunctionOperator} <: AbstractFunctionOperator
```

は、1つの代わりに2つの演算子を評価することを可能にします。例えば、OperatorPair{Identity,Gradient}のように。
