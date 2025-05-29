```
commutator(A::QuantumObject, B::QuantumObject; anti::Bool=false)
```

Return the commutator (or `anti`-commutator) of the two [`QuantumObject`](@ref):

  * commutator (`anti=false`): $\hat{A}\hat{B}-\hat{B}\hat{A}$
  * anticommutator (`anti=true`): $\hat{A}\hat{B}+\hat{B}\hat{A}$

Note that `A` and `B` must be [`Operator`](@ref)
