```
sigmaz([T=ComplexF64,] b::SpinBasis)
```

Angular momentum $σ_z$ operator for the given `SpinBasis`. For `SpinBasis(1//2)` this is the Pauli $Z$ operator while for higher spins this is the Hermitian operator that gives the quantized angular momentum observable along the $z$ direction.

See [`pauliz`](@ref) for the generalization of the qubit pauli operators to qudits while preserving them being unitary instead of Hermitian.
