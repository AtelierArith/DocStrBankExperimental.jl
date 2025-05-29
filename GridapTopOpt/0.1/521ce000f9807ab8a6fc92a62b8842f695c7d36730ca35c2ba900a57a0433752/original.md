```
struct AugmentedLagrangian <: Optimiser
```

An augmented Lagrangian method based on Nocedal and Wright, 2006 ([link](https://doi.org/10.1007/978-0-387-40065-5)). Note that this method will function as a Lagrangian method if no constraints are defined in `problem::PDEConstrainedFunctionals`.

# Parameters

  * `problem::PDEConstrainedFunctionals`: The objective and constraint setup.
  * `ls_evolver::LevelSetEvolution`: Solver for the evolution and reinitisation equations.
  * `vel_ext::VelocityExtension`: The velocity-extension method for extending  shape sensitivities onto the computational domain.
  * `history::OptimiserHistory{Float64}`: Historical information for optimisation problem.
  * `converged::Function`: A function to check optimiser convergence.
  * `has_oscillations::Function`: A function to check for oscillations.
  * `params::NamedTuple`: Optimisation parameters.

The `has_oscillations` function has been added to avoid oscillations in the  iteration history. By default this uses a mean zero crossing algorithm as implemented in ChaosTools. Oscillations checking can be disabled by taking `has_oscillations = (args...) -> false`.
