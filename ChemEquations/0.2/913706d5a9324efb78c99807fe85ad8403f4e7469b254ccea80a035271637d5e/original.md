```julia
elements(
    equation::ChemEquations.ChemEquation
) -> Vector{String}

```

Returns chemical equation's unique elements.

# Examples

```jldoctest
julia> elements(ce"2 H2 + O2 → 2 H2O")
2-element Array{String,1}:
 "H"
 "O"
```
