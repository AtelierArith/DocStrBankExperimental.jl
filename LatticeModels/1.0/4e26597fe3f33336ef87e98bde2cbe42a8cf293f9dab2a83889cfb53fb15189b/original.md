```
groundstate(eig::HamiltonianEigensystem)
groundstate(ham::Hamiltonian)
```

Finds the ground state of a Hamiltonian. Returns the state.

## Example

```julia
eig = diagonalize(ham)
ψ = groundstate(eig)
```
