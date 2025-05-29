```julia
parameter_dependencies(
    sys::ModelingToolkit.AbstractSystem
) -> Any

```

Get the parameter dependencies of the system `sys` and its subsystems.

See also [`defaults`](@ref) and [`ModelingToolkit.get_parameter_dependencies`](@ref).
