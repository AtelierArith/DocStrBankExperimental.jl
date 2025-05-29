```
quantum_chemistry_hamiltonian(E0::Number, K::AbstractMatrix{<:Number}, V::AbstractArray{<:Number,4}, [elt::Type{<:Number}=ComplexF64])
```

MPO for the quantum chemistry Hamiltonian, with kinetic energy $K$ and potential energy $V$. The Hamiltonian is given by

$$
H = E0 + \sum_{i,j} \sum_s K[i,j] e_{i,s}^{+} e_{j,s}^{-} + \sum_{i,j,k,l} \sum_{s,t} V[i,j,k,l] e_{i,s}^{+} e_{j,t}^{+} e_{k,t}^{-} e_{l,s}^{-}
$$

where $s$ and $t$ are spin indices, which can be $\uparrow$ or $\downarrow$. The full hamiltonian has `U₁ ⊠ SU₂ ⊠ FermionParity` symmetry.

!!! note
    This should not be regarded as state-of-the-art quantum chemistry DMRG code. It is only meant to demonstrate the use of MPSKit for quantum chemistry. In particular:

      * No attempt was made to incorporate spacegroup symmetries
      * MPSKit does not contain many required algorithms in quantum chemistry (orbital ordering/optimization)
      * MPOHamiltonian is not well suited for quantum chemistry

