```julia
==(
    compound_1::ChemEquations.Compound,
    compound_2::ChemEquations.Compound
) -> Bool

```

二つの化合物が化学的に等しいかどうかを確認します。

# 例

```jldoctest
julia> cc"MgOHOH" == cc"Mg(OH)2"
true
```
