```
    mutable struct Parameters{PPHY <: AbstractEmptyParams, PSIM <: AbstractEmptyParams, PHY <: AbstractEmptyParams,
                    PSOL <: AbstractEmptyParams, PUDE <: AbstractEmptyParams, PINV <: AbstractEmptyParams}
```

A mutable struct that holds various parameter sets for different aspects of a simulation or model.

# Fields

  * `physical::PPHY`: Physical parameters.
  * `simulation::PSIM`: Simulation parameters.
  * `hyper::PHY`: Hyperparameters.
  * `solver::PSOL`: Solver parameters.
  * `UDE::PUDE`: Universal Differential Equation (UDE) parameters.
  * `inversion::PINV`: Inversion parameters.

# Type Parameters

  * `PPHY`: Type of the physical parameters, must be a subtype of `AbstractEmptyParams`.
  * `PSIM`: Type of the simulation parameters, must be a subtype of `AbstractEmptyParams`.
  * `PHY`: Type of the hyperparameters, must be a subtype of `AbstractEmptyParams`.
  * `PSOL`: Type of the solver parameters, must be a subtype of `AbstractEmptyParams`.
  * `PUDE`: Type of the UDE parameters, must be a subtype of `AbstractEmptyParams`.
  * `PINV`: Type of the inversion parameters, must be a subtype of `AbstractEmptyParams`.
