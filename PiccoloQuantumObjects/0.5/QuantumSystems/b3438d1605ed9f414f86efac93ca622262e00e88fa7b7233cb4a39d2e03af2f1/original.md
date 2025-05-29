```
TimeDependentQuantumSystem <: AbstractQuantumSystem
```

A struct for storing time-dependent quantum dynamics.

# Fields

  * `H::Function`: The Hamiltonian function with time: (a, t) -> H(a, t).
  * `G::Function`: The isomorphic generator function with time, (a, t) -> G(a, t).
  * `n_drives::Int`: The number of drives in the system.
  * `levels::Int`: The number of levels in the system.
  * `params::Dict{Symbol, Any}`: A dictionary of parameters.
