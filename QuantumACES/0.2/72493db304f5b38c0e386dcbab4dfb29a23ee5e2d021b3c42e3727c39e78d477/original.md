```
get_paulis(n::Integer)
```

Returns a list of all n-qubit Paulis ordered lexicographically according to their bit string representation described in [`Pauli`](@ref). For single-qubit gates, the Pauli error probabilities are ordered as `I`, `X`, `Z`, `Y`. For two-qubit gates, the Pauli error probabilities are ordered as `II`, `XI`, `IX`, `XX`, `ZI`, `YI`, `ZX`, `YX`, `IZ`, `XZ`, `IY`, `XY`, `ZZ`, `YZ`, `ZY`, `YY`.
