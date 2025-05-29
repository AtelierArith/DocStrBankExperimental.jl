```julia
mutable struct Annealing{constant_hamiltonian} <: OpenQuantumBase.AbstractAnnealing{constant_hamiltonian}
```

`Annealing` type defines the evolution of a time-dependent Hamiltonian in both closed-system and open-system settings. It is called `Annealing` because HOQST started as a toolbox for quantum annealing.

# Fields

  * `H`: Hamiltonian for the annealing.
  * `u0`: Initial state for the annealing.
  * `annealing_parameter`: Function of annealing parameter s wrt to t
  * `interactions`: A system bath interaction set.
