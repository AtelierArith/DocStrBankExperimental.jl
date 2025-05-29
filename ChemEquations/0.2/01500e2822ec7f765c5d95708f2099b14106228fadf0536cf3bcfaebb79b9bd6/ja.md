```julia
equationmatrix(
    equation::ChemEquations.ChemEquation{T}
) -> Union{Array{Float64, 3}, Matrix}

```

原子に対応する行と化合物に対応する列を持つ方程式行列を作成します。

# 例

```jldoctest
julia> equationmatrix(ce"H2 + Cl2 → HCl")
2×3 Array{Int64,2}:
 2  0  1
 0  2  1
```
