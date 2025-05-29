```
SDeMo.SDM(::Type{TF}, ::Type{CF}, predictors::Vector{SDMLayer{T}}, presences::SDMLayer{Bool}, absences::SDMLayer{Bool}) where {TF <: Transformer, CF <: Classifier, T <: Number}
```

予測因子の配列、存在のブールレイヤー、および不在のブールレイヤーに基づいてSDMを返します。
