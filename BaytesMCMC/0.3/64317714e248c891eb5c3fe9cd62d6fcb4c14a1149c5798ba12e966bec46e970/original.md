```julia
struct Hamiltonian{E<:BaytesMCMC.KineticEnergy, D<:BaytesDiff.DiffObjective}
```

Hamiltonian struct that holds Kinetic energy and log target density function.

# Fields

  * `K::BaytesMCMC.KineticEnergy`: The kinetic energy specification.
  * `objective::BaytesDiff.DiffObjective`: Differentiable log target density of model, see BaytesDiff.
