```julia
elements(
    equation::ChemEquations.ChemEquation
) -> Vector{String}

```

化学方程式のユニークな元素を返します。

# 例

```jldoctest
julia> elements(ce"2 H2 + O2 → 2 H2O")
2-element Array{String,1}:
 "H"
 "O"
```
