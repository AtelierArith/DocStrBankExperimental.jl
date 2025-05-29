```
constraints_level_aux(m, n::Storage, 𝒯, 𝒫, modeltype::EnergyModel)
constraints_level_aux(m, n::RefStorage{AccumulatingEmissions}, 𝒯, 𝒫, modeltype::EnergyModel)
```

汎用の `Storage` ノードのレベルに対する Δ 制約を作成するための関数です。`EnergyModelsBase` は `RefStorage{AccumulatingEmissions}` に対するメソッドも提供します。
