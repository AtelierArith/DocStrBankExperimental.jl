```julia
elements(compound::ChemEquations.Compound) -> Vector{String}

```

化合物の元素を文字列として返します。

# 例

```jldoctest
julia> elements(cc"CH3COOH")
3-element Array{String,1}:
 "C"
 "H"
 "O"
```
