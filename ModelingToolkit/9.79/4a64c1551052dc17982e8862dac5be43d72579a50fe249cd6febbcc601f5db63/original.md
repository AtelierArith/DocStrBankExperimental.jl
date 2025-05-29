```julia
observed(sys::ModelingToolkit.AbstractSystem) -> Any

```

Get the observed equations of the system `sys` and its subsystems. These can be expressed in terms of `unknowns(sys)`, and do not have to be explicitly solved for.

See also [`observables`](@ref) and [`ModelingToolkit.get_observed()`](@ref).
