```
findgroundstate(eig::HamiltonianEigensystem)
findgroundstate(ham::Hamiltonian)
```

Finds the ground state of a Hamiltonian. Returns the energy and the state.

## Example

```julia
eig = diagonalize(ham)
E, ψ = findgroundstate(eig)
```
