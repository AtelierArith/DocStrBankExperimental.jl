```
create_node(m, n::Source, 𝒯, 𝒫, modeltype::EnergyModel)
```

`Source`のすべての制約を設定します。指定されていないすべての`Source`のサブタイプのフォールバックオプションとして機能します。

# 呼び出された制約関数

  * [`constraints_data`](@ref) すべての `node_data(n)` のために、
  * [`constraints_flow_out`](@ref),
  * [`constraints_capacity`](@ref),
  * [`constraints_opex_fixed`](@ref), および
  * [`constraints_opex_var`](@ref).
