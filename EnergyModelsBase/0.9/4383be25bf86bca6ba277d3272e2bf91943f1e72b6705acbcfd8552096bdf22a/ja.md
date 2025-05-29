```
create_node(m, n::NetworkNode, 𝒯, 𝒫, modeltype::EnergyModel)
```

`NetworkNode`のすべての制約を設定します。指定されていないすべての`NetworkNode`のサブタイプのフォールバックオプションとして機能します。

# 呼び出される制約関数

  * [`constraints_data`](@ref) すべての `node_data(n)` に対して、
  * [`constraints_flow_in`](@ref),
  * [`constraints_flow_out`](@ref),
  * [`constraints_capacity`](@ref),
  * [`constraints_opex_fixed`](@ref)、および
  * [`constraints_opex_var`](@ref)。
