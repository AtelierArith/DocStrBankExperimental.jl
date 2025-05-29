```julia
read_realized_expression(
    res::PowerSimulations.SimulationProblemResults,
    expression::AbstractString;
    kwargs...
) -> Any

```

Return the final values for the requested expression for each time step for a problem.

Refer to [`read_realized_variable`](@ref) for help and examples.
