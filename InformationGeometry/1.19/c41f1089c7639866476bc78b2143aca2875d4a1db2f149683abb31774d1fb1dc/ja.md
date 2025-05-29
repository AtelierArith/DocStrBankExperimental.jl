```
DetermineDmodel(DS::AbstractDataSet, model::Function; ADmode::Union{Symbol,Val}=:ForwardDiff)::Function
```

データセットの x 値と y 値の形式に応じて、パラメータ `θ` に関する `model(x,θ)` の自動微分を構成する適切な関数を返します。
