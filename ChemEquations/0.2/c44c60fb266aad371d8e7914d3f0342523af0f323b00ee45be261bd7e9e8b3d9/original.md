```julia
==(
    equation_1::ChemEquations.ChemEquation,
    equation_2::ChemEquations.ChemEquation
) -> Any

```

Checks whether two equations are chemically equal.

# Examples

```jldoctest
julia> ce"H2 + O2 = H2O" == ce"O2 + H2 → H2O"
true
```
