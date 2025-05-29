```
commutator(A::QuantumObject, B::QuantumObject; anti::Bool=false)
```

2つの [`QuantumObject`](@ref) の交換子（または `anti`-交換子）を返します：

  * 交換子 (`anti=false`): $\hat{A}\hat{B}-\hat{B}\hat{A}$
  * 反交換子 (`anti=true`): $\hat{A}\hat{B}+\hat{B}\hat{A}$

`A` と `B` は [`Operator`](@ref) でなければなりません。
