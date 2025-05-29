```
QuantumSystem <: AbstractQuantumSystem
```

A struct for storing quantum dynamics.

# Fields

  * `H::Function`: The Hamiltonian function, excluding dissipation: a -> H(a).
  * `G::Function`: The isomorphic generator function, including dissipation, a -> G(a).
  * `levels::Int`: The number of levels in the system.
  * `n_drives::Int`: The number of drives in the system.
