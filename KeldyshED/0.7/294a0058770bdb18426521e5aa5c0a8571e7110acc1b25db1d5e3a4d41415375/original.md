```julia
EDCore(
    hamiltonian::KeldyshED.Operators.OperatorExpr{S<:Number},
    soi::KeldyshED.Hilbert.SetOfIndices;
    symmetry_breakers
) -> KeldyshED.EDCore

```

Reduce a given Hamiltonian to a block-diagonal form and diagonalize it.

This constructor uses the [`autopartition procedure`](@ref autopartition), and the QR algorithm to diagonalize the blocks. The invariant subspaces of the Hamiltonian are chosen such that all creation and annihilation operators carrying compound indices from the provided set `soi` map one subspace to one subspace.

It is possible to pass an optional list of operator expressions (`symmetry_breakers`) that are required to share invariant subspaces with the Hamiltonian. As those operators can break some symmetries of the Hamiltonian, taking them into account can result in a less refined subspace partition and block structure.
