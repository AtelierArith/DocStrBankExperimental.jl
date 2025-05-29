```julia
equations(sys::ModelingToolkit.AbstractSystem) -> Any

```

Get the flattened equations of the system `sys` and its subsystems. It may include some abbreviations and aliases of observables. It is often the most useful way to inspect the equations of a system.

See also [`full_equations`](@ref) and [`ModelingToolkit.get_eqs`](@ref).
