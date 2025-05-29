```
create_node(m, n::Sink, 𝒯, 𝒫, modeltype::EnergyModel)
```

`Sink`のすべての制約を設定します。指定されていないすべての`Sink`のサブタイプのフォールバックオプションとして機能します。

# 呼び出される制約関数

  * [`constraints_data`](@ref) for all `node_data(n)`,
  * [`constraints_flow_in`](@ref),
  * [`constraints_capacity`](@ref),
  * [`constraints_opex_fixed`](@ref), and
  * [`constraints_opex_var`](@ref).
