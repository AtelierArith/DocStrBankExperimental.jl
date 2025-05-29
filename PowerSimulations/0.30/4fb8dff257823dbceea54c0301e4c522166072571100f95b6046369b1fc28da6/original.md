```julia
read_realized_dual(
    res::PowerSimulations.SimulationProblemResults,
    dual::AbstractString;
    kwargs...
) -> Any

```

Return the final values for the requested dual for each time step for a problem.

Refer to [`read_realized_variable`](@ref) for help and examples.
