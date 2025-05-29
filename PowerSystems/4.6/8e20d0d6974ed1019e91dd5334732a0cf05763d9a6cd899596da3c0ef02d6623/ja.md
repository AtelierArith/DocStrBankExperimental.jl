```julia
show_components(
    sys::PowerSystems.System,
    component_type::Type{<:PowerSystems.Component};
    ...
)
show_components(
    sys::PowerSystems.System,
    component_type::Type{<:PowerSystems.Component},
    additional_columns::Union{Dict, Vector};
    kwargs...
)

```

指定されたタイプのすべてのコンポーネントをテーブルで表示します。

# 引数

  * `sys::System`: コンポーネントを含むシステム。
  * `component_type::Type{<:Component}`: 表示するタイプ。具体的なタイプでなければなりません。
  * `additional_columns::Union{Dict, Vector}`: 表示する追加の列。Dictオプションは列名から関数へのマッピングです。関数はコンポーネントを受け入れなければなりません。Vectorオプションは`component_type`のフィールド名の配列です。

追加のキーワード引数はPrettyTables.pretty_tableに転送されます。

# 例

```julia
show_components(sys, ThermalStandard)
show_components(sys, ThermalStandard, Dict("has_time_series" => x -> has_time_series(x)))
show_components(sys, ThermalStandard, [:active_power, :reactive_power])
```
