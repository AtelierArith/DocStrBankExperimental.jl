```julia
read_realized_variables(
    res::PowerSimulations.SimulationProblemResults;
    kwargs...
) -> Dict

```

Return the final values for the requested variables for each time step for a problem.

Decision problem results are returned in a Dict{String, Dict{DateTime, DataFrame}}.

Emulation problem results are returned in a Dict{String, DataFrame}.

Limit the data sizes returned by specifying `initial_time` and `count` for decision problems or `start_time` and `len` for emulation problems.

If the Julia process is started with multiple threads, the code will read the variables in parallel.

See also [`load_results!`](@ref) to preload data into memory.

# Arguments

  * `variables::Vector{Union{String, Tuple}}`: Variable name as a string or a Tuple with variable type and device type. If not provided then return all variables.
  * `initial_time::Dates.DateTime`: Initial time of the requested results. Decision problems only.
  * `count::Int`: Number of results. Decision problems only.
  * `start_time::Dates.DateTime`: Start time of the requested results. Emulation problems only.
  * `len::Int`: Number of rows in each DataFrame. Emulation problems only.

# Examples

```julia
julia > variables_as_strings =
    ["ActivePowerVariable__ThermalStandard", "ActivePowerVariable__RenewableDispatch"]
julia > variables_as_types =
    [(ActivePowerVariable, ThermalStandard), (ActivePowerVariable, RenewableDispatch)]
julia > read_realized_variables(results, variables_as_strings)
julia > read_realized_variables(results, variables_as_types)
```
