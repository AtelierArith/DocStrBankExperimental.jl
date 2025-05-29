```
paulix([T=ComplexF64,] b::NLevelBasis, pow=1)
```

Generalized Pauli $X$ operator for the given `N` level system. This is also called the shift matrix, and generalizes the qubit pauli matrices to qudits, while preserving the operators being unitary. A different generalization is given by the angular momentum operators which preserves the operators being Hermitian and is implemented for the `SpinBasis` (see [`sigmax`](@ref)).

Powers of `paulix` together with [`pauliz`](@ref) form a complete, orthornormal (under Hilbert–Schmidt norm) operator basis.

Returns `X^pow`.
