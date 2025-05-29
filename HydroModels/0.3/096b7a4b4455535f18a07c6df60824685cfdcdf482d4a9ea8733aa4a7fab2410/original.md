```
(route::RapidRoute)(input::Array, params::ComponentVector; kwargs...)
```

Executes the RAPID routing simulation.

# Arguments

  * `input::Array`: Lateral inflow data, typically shape (1, nodes, timesteps) where the variable is inflow.
  * `params::ComponentVector`: Parameters containing `:rapid_k` and `:rapid_x` for each node.

# Keyword Arguments

  * `delta_t::Float64`: Simulation time step in seconds (default: 1.0).
  * `device`: Computing device (e.g., `identity` for CPU, `gpu` function). Default `identity`.
  * `ptyidx`: Indices mapping parameters to nodes. Default `1:num_nodes`.
  * `interp`: Interpolation method for time-varying inputs. Default `DirectInterpolation`.
  * `solver`: ODE solver instance. Default `ManualSolver(mutable=true)`.
  * `timeidx`: Time indices for the simulation. Default `1:time_len`.
  * `initstates`: Initial discharge values. Default zeros.

# Returns

  * `AbstractArray{T,3}`: Output array of discharge, shape (1, nodes, timesteps).

# Example

```julia
# Assuming 'rapid_route' is a RapidRoute instance
discharge = rapid_route(lateral_inflow, parameters; delta_t=3600.0)
```

# Notes

  * Solves the Muskingum-Cunge equations using a matrix-based approach.
  * Calculates Muskingum coefficients (c0, c1, c2) internally based on `k`, `x`, and `delta_t`.
  * Requires `input` to be 3D (variables, nodes, time).
