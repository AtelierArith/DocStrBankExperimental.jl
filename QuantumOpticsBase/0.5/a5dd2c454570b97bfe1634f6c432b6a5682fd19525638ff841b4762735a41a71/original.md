```
pauliz([T=ComplexF64,] b::NLevelBasis, pow=1)
```

Generalized Pauli $Z$ operator for the given `N` level system. This is also called the clock matrix, and generalizes the qubit pauli matrices to qudits, while preserving the operators being unitary. A different generalization is given by the angular momentum operators which preserves the operators being Hermitian and is implemented for the `SpinBasis` (see [`sigmaz`](@ref)).

Powers of `pauliz` together with [`paulix`](@ref) form a complete, orthornormal (under Hilbert–Schmidt norm) operator basis.

Returns `Z^pow`.
