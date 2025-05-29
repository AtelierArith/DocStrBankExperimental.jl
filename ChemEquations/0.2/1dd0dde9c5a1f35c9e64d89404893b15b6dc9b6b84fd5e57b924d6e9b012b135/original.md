```julia
string(equation::ChemEquations.ChemEquation) -> String

```

Creates a string to represent the chemical equation.

All compounds are displayed with [`Base.string(::Compound)`](@ref), in the order in which they were originally given, with coefficients equal to 1 not displayed. `'='` and `'+'` are used as separators, with spaces inserted for easier reading.

# Examples

```jldoctest
julia> string(ce"Cr2O7{2-} + H{+} + {-} = Cr{3+} + H2O")
"Cr2O7{-2} + H{+} + e = Cr{+3} + H2O"
```
