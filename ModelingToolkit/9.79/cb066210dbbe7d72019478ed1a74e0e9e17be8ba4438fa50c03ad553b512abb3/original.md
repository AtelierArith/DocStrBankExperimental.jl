```julia
parameters(
    sys::ModelingToolkit.AbstractSystem;
    initial_parameters
) -> Vector{Any}

```

Get the parameters of the system `sys` and its subsystems.

See also [`@parameters`](@ref) and [`ModelingToolkit.get_ps`](@ref).
