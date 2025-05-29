```julia
full_equations(
    sys::ModelingToolkit.AbstractSystem;
    simplify
) -> Any

```

Like `equations(sys)`, but includes substitutions done by the tearing process. These equations matches generated numerical code.

See also [`equations`](@ref) and [`ModelingToolkit.get_eqs`](@ref).
