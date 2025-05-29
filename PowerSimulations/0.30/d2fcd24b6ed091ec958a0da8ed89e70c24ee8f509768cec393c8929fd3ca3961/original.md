```julia
read_realized_variable(
    res::PowerSimulations.SimulationProblemResults,
    variable::AbstractString;
    kwargs...
) -> Any

```

Return the final values for the requested variable for each time step for a problem.

Decision problem results are returned in a Dict{DateTime, DataFrame}.

Emulation problem results are returned in a DataFrame.

Limit the data sizes returned by specifying `initial_time` and `count` for decision problems or `start_time` and `len` for emulation problems.

See also [`load_results!`](@ref) to preload data into memory.

# Arguments

  * `variable::Union{String, Tuple}`: Variable name as a string or a Tuple with variable type and device type.
  * `initial_time::Dates.DateTime`: Initial time of the requested results. Decision problems only.
  * `count::Int`: Number of results. Decision problems only.
  * `start_time::Dates.DateTime`: Start time of the requested results. Emulation problems only.
  * `len::Int`: Number of rows in each DataFrame. Emulation problems only.

# Examples

```julia
julia > read_realized_variable(results, "ActivePowerVariable__ThermalStandard")
julia > read_realized_variable(results, (ActivePowerVariable, ThermalStandard))
```
