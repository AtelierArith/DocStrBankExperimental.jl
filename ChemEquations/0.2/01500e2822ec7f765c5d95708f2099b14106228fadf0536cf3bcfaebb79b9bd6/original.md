```julia
equationmatrix(
    equation::ChemEquations.ChemEquation{T}
) -> Union{Array{Float64, 3}, Matrix}

```

Creates an equation matrix in which rows correspond to atoms and columns correspond to compounds.

# Examples

```jldoctest
julia> equationmatrix(ce"H2 + Cl2 → HCl")
2×3 Array{Int64,2}:
 2  0  1
 0  2  1
```
