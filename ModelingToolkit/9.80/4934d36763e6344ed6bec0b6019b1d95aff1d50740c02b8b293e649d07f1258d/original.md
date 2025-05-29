```julia
defaults(sys::ModelingToolkit.AbstractSystem) -> Any

```

Get the default values of the system sys and its subsystems. If they are not explicitly provided, variables and parameters are initialized to these values.

See also [`initialization_equations`](@ref), [`parameter_dependencies`](@ref) and [`ModelingToolkit.get_defaults`](@ref).
