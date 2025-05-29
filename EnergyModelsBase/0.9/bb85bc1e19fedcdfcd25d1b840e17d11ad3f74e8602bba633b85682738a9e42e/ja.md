```
constraints_capacity(m, n::Node, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_capacity(m, n::Storage, 𝒯::TimeStructure, modeltype::EnergyModel)
constraints_capacity(m, n::Sink, 𝒯::TimeStructure, modeltype::EnergyModel)
```

汎用の[`Node`](@ref)、[`Storage`](@ref)、および[`Sink`](@ref)の最大容量に関する制約を作成するための関数です。

これらの関数は、特定の`Node`に対して他のメソッドが指定されていない場合のフォールバックオプションとして機能します。

!!! warning "この関数のディスパッチ"
    この関数の新しいメソッドを作成する場合、投資オプションを含めたい場合は、必ずその関数内で`constraints_capacity_installed(m, n, 𝒯, modeltype)`を呼び出すことが重要です。

