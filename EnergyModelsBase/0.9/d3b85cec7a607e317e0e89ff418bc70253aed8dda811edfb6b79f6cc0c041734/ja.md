```
constraints_flow_in(m, n, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_flow_in(m, n::Storage, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_flow_in(m, n::Storage{AccumulatingEmissions}, 𝒯::TimeStructure, modeltype::EnergyModel)
```

汎用の [`Node`](@ref) または [`Storage`](@ref) からの出口フローに対する制約を作成するための関数です。

これらの関数は、特定の `Node` に対して他のメソッドが指定されていない場合のフォールバックオプションとして機能します。
