```julia
complete(sys::ModelingToolkit.AbstractSystem) -> Any

```

Mark a system as completed. If a system is complete, the system will no longer namespace its subsystems or variables, i.e. `isequal(complete(sys).v.i, v.i)`.
