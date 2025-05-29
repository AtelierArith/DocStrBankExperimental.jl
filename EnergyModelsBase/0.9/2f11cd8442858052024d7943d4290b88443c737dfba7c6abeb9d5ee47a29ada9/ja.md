```
create_node(m, n::Storage, 𝒯, 𝒫, modeltype::EnergyModel)
```

`Storage`のすべての制約を設定します。指定されていないすべての`Storage`のサブタイプのフォールバックオプションとして機能します。

# 呼び出される制約関数

  * [`constraints_level`](@ref)
  * [`constraints_data`](@ref) for all `node_data(n)`,
  * [`constraints_flow_in`](@ref),
  * [`constraints_flow_out`](@ref),
  * [`constraints_capacity`](@ref),
  * [`constraints_opex_fixed`](@ref), and
  * [`constraints_opex_var`](@ref).
