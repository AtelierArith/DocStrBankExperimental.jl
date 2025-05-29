```
SciMLOperators.isconstant(A::AbstractQuantumObject)
```

Test whether the [`AbstractQuantumObject`](@ref) `A` is constant in time. For a [`QuantumObject`](@ref), this function returns `true`, while for a [`QuantumObjectEvolution`](@ref), this function returns `true` if the operator is constant in time.
