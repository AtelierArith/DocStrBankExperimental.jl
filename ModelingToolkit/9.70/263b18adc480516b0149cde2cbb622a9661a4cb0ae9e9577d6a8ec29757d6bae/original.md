```julia
complete(
    sys::ModelingToolkit.AbstractSystem;
    split,
    flatten,
    add_initial_parameters
) -> Any

```

Mark a system as completed. A completed system is a system which is done being defined/modified and is ready for structural analysis or other transformations. This allows for analyses and optimizations to be performed which require knowing the global structure of the system.

One property to note is that if a system is complete, the system will no longer namespace its subsystems or variables, i.e. `isequal(complete(sys).v.i, v.i)`.
