```
AugmentedLagrangian(
  problem    :: PDEConstrainedFunctionals{N},
  ls_evolver :: LevelSetEvolution,
  vel_ext    :: VelocityExtension,
  φ0;
  Λ_max = 10^10, ζ = 1.1, update_mod = 5, γ = 0.1, γ_reinit = 0.5, os_γ_mult = 0.75,
  maxiter = 1000, verbose=false, constraint_names = map(i -> Symbol("C_$i"),1:N),
  converged::Function = default_al_converged, debug = false,
  has_oscillations::Function = default_has_oscillations
) where {N,O}
```

Create an instance of `AugmentedLagrangian` with several adjustable defaults.

# Required

  * `problem::PDEConstrainedFunctionals`: The objective and constraint setup.
  * `ls_evolver::LevelSetEvolution`: Solver for the evolution and reinitisation equations.
  * `vel_ext::VelocityExtension`: The velocity-extension method for extending  shape sensitivities onto the computational domain.
  * `φ0`: An initial level-set function defined as a FEFunction or GridapDistributed equivilent.

# Optional defaults

  * `γ = 0.1`: Initial coeffient on the time step size for solving the Hamilton-Jacobi evolution equation.
  * `γ_reinit = 0.5`: Coeffient on the time step size for solving the reinitisation equation.
  * `ζ = 1.1`: Increase multiplier on Λ every `update_mod` iterations.
  * `Λ_max = 5.0`: Maximum value on any entry in Λ.
  * `update_mod = 5`: Number of iterations before increasing `Λ`.
  * `reinit_mod = 1`: How often we solve reinitialisation equation.
  * `maxiter = 1000`: Maximum number of algorithm iterations.
  * `verbose=false`: Verbosity flag.
  * `constraint_names = map(i -> Symbol("C_$i"),1:N)`: Constraint names for history output.
  * `has_oscillations::Function = default_has_oscillations`: Function to check for oscillations  in the history.
  * `initial_parameters::Function = default_al_init_params`: Function to generate initial λ, Λ. This can be replaced to inject different λ and Λ, for example.
  * `os_γ_mult = 0.75`: Decrease multiplier for `γ` when `has_oscillations` returns true
  * `converged::Function = default_hp_converged`: Convergence criteria.
  * `debug = false`: Debug flag.
