```julia
read_realized_parameter(
    res::PowerSimulations.SimulationProblemResults,
    parameter::AbstractString;
    kwargs...
) -> Any

```

Return the final values for the requested parameter for each time step for a problem.

Refer to [`read_realized_variable`](@ref) for help and examples.
