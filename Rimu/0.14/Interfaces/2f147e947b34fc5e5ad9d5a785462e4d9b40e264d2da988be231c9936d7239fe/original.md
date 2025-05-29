```
random_offdiagonal(offdiagonals::AbstractOffdiagonals)
random_offdiagonal(ham::AbstractHamiltonian, address)
-> newaddress, probability, matrixelement
```

Generate a single random excitation, i.e. choose from one of the accessible off-diagonal elements in the column corresponding to `address` in the Hamiltonian matrix represented by `ham`. Alternatively, pass as argument an iterator over the accessible matrix elements.

Part of the [`AbstractHamiltonian`](@ref) interface.
