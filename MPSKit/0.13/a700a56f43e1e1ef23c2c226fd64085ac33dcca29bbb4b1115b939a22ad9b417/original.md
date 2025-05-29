```
exact_diagonalization(H::FiniteMPOHamiltonian;
                      sector=first(sectors(oneunit(physicalspace(H, 1)))),
                      len::Int=length(H), num::Int=1, which::Symbol=:SR,
                      alg=Defaults.alg_eigsolve(; dynamic_tols=false))
                        -> vals, state_vecs, convhist
```

Use [`KrylovKit.eigsolve`](@extref) to perform exact diagonalization on a `FiniteMPOHamiltonian` to find its eigenvectors as `FiniteMPS` of maximal rank, essentially equivalent to dense eigenvectors.

### Arguments

  * `H::FiniteMPOHamiltonian`: the Hamiltonian to diagonalize.

### Keyword arguments

  * `sector=first(sectors(oneunit(physicalspace(H, 1))))`: the total charge of the eigenvectors, which is chosen trivial by default.
  * `len::Int=length(H)`: the length of the system.
  * `num::Int=1`: the number of eigenvectors to find.
  * `which::Symbol=:SR`: the kind eigenvalues to find, see [`KrylovKit.eigsolve`](@extref).
  * `alg=Defaults.alg_eigsolve(; dynamic_tols=false)`: the diagonalization algorithm to use, see [`KrylovKit.eigsolve`](@extref).

!!! note "Valid `sector` values"
    The total charge of the eigenvectors is imposed by adding a charged auxiliary space as the leftmost virtualspace of each eigenvector. Specifically, this is achieved by passing `left=Vect[typeof(sector)](sector => 1)` to the [`FiniteMPS`](@ref) constructor. As such, the only valid `sector` values (i.e. `sector` values for which the corresponding eigenstates have valid fusion channels) are those that occur in the dual of the fusion of all the physical spaces in the system.

