```
HydroRoute{N} <: AbstractHydroRoute
```

Represents a hydrological routing component using customizable flux equations.

# Fields

  * `rfluxes::Vector{<:AbstractFlux}`: Flux functions defining routing processes (e.g., outflow calculation).
  * `multi_flux_func::Function`: Compiled function to evaluate all non-state-derivative fluxes.
  * `multi_ode_func::Function`: Compiled function for state derivatives used by ODE solvers.
  * `aggr_func::Function`: Function to aggregate or distribute flows between connected elements (often identity or matrix multiplication).
  * `infos::NamedTuple`: Metadata (inputs, outputs, states, params, nns).

# Constructor

```julia
HydroRoute(; rfluxes, dfluxes, aggr_func, name=nothing)
```

  * `rfluxes`: Vector of routing fluxes (e.g., `HydroFlux`, `NeuralFlux`).
  * `dfluxes`: Vector of state derivative fluxes (`StateFlux`).
  * `aggr_func`: Aggregation/distribution function.
  * `name`: Optional symbol identifier.

# Notes

  * Builds specialized functions (`multi_flux_func`, `multi_ode_func`) for efficient computation.
  * Designed for use within a larger model (e.g., `HydroModel`).
  * Handles variable management and metadata tracking internally.
