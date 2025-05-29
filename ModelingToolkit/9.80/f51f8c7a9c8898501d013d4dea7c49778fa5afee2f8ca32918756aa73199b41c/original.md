```julia
guesses(sys::ModelingToolkit.AbstractSystem) -> Any

```

Get the guesses for variables in the initialization system of the system `sys` and its subsystems.

See also [`initialization_equations`](@ref) and [`ModelingToolkit.get_guesses`](@ref).
