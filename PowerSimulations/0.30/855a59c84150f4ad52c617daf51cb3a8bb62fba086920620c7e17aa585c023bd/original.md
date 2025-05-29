```julia
read_realized_aux_variable(
    res::PowerSimulations.SimulationProblemResults,
    aux_variable::AbstractString;
    kwargs...
) -> Any

```

Return the final values for the requested auxiliary variable for each time step for a problem.

Refer to [`read_realized_variable`](@ref) for help and examples.
