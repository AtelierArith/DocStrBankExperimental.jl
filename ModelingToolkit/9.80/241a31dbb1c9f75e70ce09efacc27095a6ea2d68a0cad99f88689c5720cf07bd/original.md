```julia
initialization_equations(
    sys::ModelingToolkit.AbstractSystem
) -> Any

```

Get the initialization equations of the system `sys` and its subsystems.

See also [`guesses`](@ref), [`defaults`](@ref), [`parameter_dependencies`](@ref) and [`ModelingToolkit.get_initialization_eqs`](@ref).
