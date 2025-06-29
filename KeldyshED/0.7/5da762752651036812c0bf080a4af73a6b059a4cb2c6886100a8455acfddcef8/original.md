Lightweight Exact Diagonalization solver for finite systems of fermions.

## Fields

  * `full_hs::KeldyshED.Hilbert.FullHilbertSpace`: Full Hilbert space of the system.
  * `subspaces::Vector{KeldyshED.Hilbert.HilbertSubspace}`: List of the invariant subspaces of the Hamiltonian.
  * `eigensystems::Vector{KeldyshED.EigenSystem}`: Eigensystems of the Hamiltonian within the invariant subspaces.
  * `creation_connection::Vector{Dict{Int64, Int64}}`: Subspace-to-subspace connections generated by the creation operators $c^\dagger_i$. If a creation operator, whose compound index $i$ translates into a linear index `l` by `full_hs.soi`, acts between subspaces $s$ and $s'$, then `creation_connection[l][s] = s'`.

  * `annihilation_connection::Vector{Dict{Int64, Int64}}`: Subspace-to-subspace connections generated by the annihilation operators $c_i$. If an annihilation operator, whose compound index $i$ translates into a linear index `l` by `full_hs.soi`, acts between subspaces $s$ and $s'$, then `annihilation_connection[l][s] = s'`.

  * `cdag_matrices::Array{Dict{Int64, Matrix{ScalarType}}, 1} where ScalarType<:Number`: Matrices of the creation operators $c^\dagger_i$ in the eigenbasis of the Hamiltonian. If a creation operator, whose compound index $i$ translates into a linear index `l` by `full_hs.soi`, acts between subspaces $s$ and $s'$, then the corresponding block of its matrix form is available as `cdag_matrices[l][s]`.

  * `c_matrices::Array{Dict{Int64, Matrix{ScalarType}}, 1} where ScalarType<:Number`: Matrices of the annihilation operators $c_i$  in the eigenbasis of the Hamiltonian. If an annihilation operator, whose compound index $i$ translates into a linear index `l` by `full_hs.soi`, acts between subspaces $s$ and $s'$, then the corresponding block of its matrix form is available as `c_matrices[l][s]`.

  * `gs_energy::Float64`: Ground state energy of the system.
