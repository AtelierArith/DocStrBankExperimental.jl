```
solve_powerflow!(data::ACPowerFlowData; pf::ACPowerFlow{<:ACPowerFlowSolverType} = ACPowerFlow(), kwargs...)
```

Solve the multiperiod AC power flow problem for the given power flow data.

The bus types can be changed from PV to PQ if the reactive power limits are violated.

# Arguments

  * `data::ACPowerFlowData`: The power flow data containing netwthe grid information and initial conditions.
  * `pf::ACPowerFlow{<:ACPowerFlowSolverType}`: The power flow solver type. Defaults to `NewtonRaphsonACPowerFlow`.
  * `kwargs...`: Additional keyword arguments.

# Keyword Arguments

  * `check_connectivity::Bool`: Checks if the grid is connected. Default is `true`.
  * 'check*reactive*power_limits': if `true`, the reactive power limits are enforced by changing the respective bus types from PV to PQ. Default is `false`.
  * `time_steps`: Specifies the time steps to solve. Defaults to sorting and collecting the keys of `data.timestep_map`.

# Description

This function solves the AC power flow problem for each time step specified in `data`.  It preallocates memory for the results and iterates over the sorted time steps.      For each time step, it calls the `_ac_powerflow` function to solve the power flow equations and updates the `data` object with the results.      If the power flow converges, it updates the active and reactive power injections, as well as the voltage magnitudes and angles for different bus types (REF, PV, PQ).      If the power flow does not converge, it sets the corresponding entries in `data` to `NaN`.      Finally, it calculates the branch power flows and updates the `data` object.

# Notes

  * If the grid topology changes (e.g., tap positions of transformers or in-service status of branches), the admittance matrices `Yft` and `Ytf` must be updated.
  * If `Yft` and `Ytf` change between time steps, the branch flow calculations must be moved inside the loop.

# Examples

```julia
solve_powerflow!(data)
```
