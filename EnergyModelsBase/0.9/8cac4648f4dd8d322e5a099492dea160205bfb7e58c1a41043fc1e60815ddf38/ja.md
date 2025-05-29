```
constraints_level(m, n::Storage, 𝒯, 𝒫, modeltype::EnergyModel)
```

`Storage`ノードのレベル制約を作成するための関数です。新しい`Storage`ノードを作成する場合は、この関数を呼び出しに含める必要があります。これは、さまざまな[`StorageBehavior`](@ref)sに必要なすべての情報を提供します。
