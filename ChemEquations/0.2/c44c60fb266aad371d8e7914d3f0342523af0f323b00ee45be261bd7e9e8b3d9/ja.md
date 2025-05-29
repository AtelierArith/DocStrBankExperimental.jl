```julia
==(
    equation_1::ChemEquations.ChemEquation,
    equation_2::ChemEquations.ChemEquation
) -> Any

```

2つの方程式が化学的に等しいかどうかをチェックします。

# 例

```jldoctest
julia> ce"H2 + O2 = H2O" == ce"O2 + H2 → H2O"
true
```
