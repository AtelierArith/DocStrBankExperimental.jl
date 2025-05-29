```julia
observables(sys::ModelingToolkit.AbstractSystem) -> Any

```

Get the observed variables of the system `sys` and its subsystems. These can be expressed in terms of `unknowns(sys)`, and do not have to be explicitly solved for. It is equivalent to all left hand sides of `observed(sys)`.

See also [`observed`](@ref).
