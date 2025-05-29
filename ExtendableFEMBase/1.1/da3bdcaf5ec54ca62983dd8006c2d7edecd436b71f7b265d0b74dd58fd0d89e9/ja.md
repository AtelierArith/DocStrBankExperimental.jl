```
abstract type OperatorPair{<:StandardFunctionOperator,<:StandardFunctionOperator} <: StandardFunctionOperator
```

は、1つの演算子の代わりに2つの演算子を評価することを可能にします。例えば、OperatorPair{Identity,Gradient}のように。
