```julia
string(compound::ChemEquations.Compound) -> String

```

Creates a string to represent the compound.

All elements are displayed only once (e.g. `"H2O"` and not `"HOH"`), in the order in which they were originally given (e.g. `"MgO2H2"` from `cc"Mg(OH)2"`), with coefficients equal to 1 not displayed (e.g. `"H"` and not `"H1"`).

# Examples

```jldoctest
julia> string(cc"CuSO4 * 5 H2O")
"CuSO9H10"
```
