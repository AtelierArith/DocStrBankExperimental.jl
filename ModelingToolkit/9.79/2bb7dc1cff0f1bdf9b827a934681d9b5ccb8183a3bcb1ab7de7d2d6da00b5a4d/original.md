```julia
independent_variables(
    sys::ModelingToolkit.AbstractSystem
) -> Vector{SymbolicUtils.BasicSymbolic{Real}}

```

Get the independent variable(s) of the system `sys`.

See also [`@independent_variables`](@ref) and [`ModelingToolkit.get_iv`](@ref).
