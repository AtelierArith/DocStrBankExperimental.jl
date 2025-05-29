```
constraints_flow_out(m, n::Node, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_flow_out(m, n::Storage, 𝒯::TimeStructure, modeltype::EnergyModel)
```

汎用の `Node` からの出口フローに関する制約を作成するための関数です。この関数は、`Node` に対して他の関数が指定されていない場合のフォールバックオプションとして機能します。
