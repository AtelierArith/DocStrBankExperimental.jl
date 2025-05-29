```julia
unknowns(sys::ModelingToolkit.AbstractSystem) -> Any

```

Get the unknown variables of the system `sys` and its subsystems. These must be explicitly solved for, unlike `observables(sys)`.

See also [`ModelingToolkit.get_unknowns`](@ref).
