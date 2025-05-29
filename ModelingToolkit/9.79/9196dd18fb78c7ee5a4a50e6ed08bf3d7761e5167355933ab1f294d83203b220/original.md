```julia
map_variables_to_equations(
    sys::ModelingToolkit.AbstractSystem;
    rename_dummy_derivatives
) -> Dict{Union{Symbolics.Num, SymbolicUtils.BasicSymbolic}, Symbolics.Equation}

```

Given a system that has been simplified via `structural_simplify`, return a `Dict` mapping variables of the system to equations that are used to solve for them. This includes observed variables.

# Keyword Arguments

  * `rename_dummy_derivatives`: Whether to rename dummy derivative variable keys into their `Differential` forms. For example, this would turn the key `yˍt(t)` into `Differential(t)(y(t))`.
