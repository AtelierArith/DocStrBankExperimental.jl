```
struct HilbertianProjection <: Optimiser
```

A Hilbertian projection method as described by Wegert et al., 2023 ([link](https://doi.org/10.1007/s00158-023-03663-0)).

# Parameters

  * `problem::PDEConstrainedFunctionals{N}`: The objective and constraint setup.
  * `ls_evolver::LevelSetEvolution`: Solver for the evolution and reinitisation equations.
  * `vel_ext::VelocityExtension`: The velocity-extension method for extending shape sensitivities onto the computational domain.
  * `projector::HilbertianProjectionMap`: Sensitivity information projector
  * `history::OptimiserHistory{Float64}`: Historical information for optimisation problem.
  * `converged::Function`: A function to check optimiser convergence.
  * `has_oscillations::Function`: A function to check for oscillations.
  * `params::NamedTuple`: Optimisation parameters.
