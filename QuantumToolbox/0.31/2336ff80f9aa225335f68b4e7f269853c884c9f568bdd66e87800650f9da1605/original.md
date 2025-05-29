```
A ⋅ B
dot(A::QuantumObject, B::QuantumObject)
```

Compute the dot product between two [`QuantumObject`](@ref): $\langle A | B \rangle$

Note that `A` and `B` should be [`Ket`](@ref) or [`OperatorKet`](@ref)

!!! note
    `A ⋅ B` (where `⋅` can be typed by tab-completing `\cdot` in the REPL) is a synonym of `dot(A, B)`.

