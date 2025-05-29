```
HydroUsageLimitFeedforward(
    component_type::Type{<:PowerSystems.Component},
    source::Type{T},
    affected_values::Vector{DataType},
    meta = CONTAINER_KEY_EMPTY_META
) where {T}
```

水エネルギーの最大使用量をソース値に基づいて強制する制約を追加します。ソースとして補助変数HydroEnergyOutputを使用し、HydroUsageLimitParameterに影響を与えることをお勧めします。

# 引数:

  * `component_type::Type{<:`[`PowerSystems.Component`](@extref)`}` : フィードフォワードが適用されるコンポーネントのタイプを指定します
  * `source::Type{T}` : フィードフォワードの値のソースとしてVariableType、ParameterTypeまたはAuxVariableTypeを指定します
  * `affected_values::Vector{DataType}` : ソース値を使用して水の制限が適用される変数を指定します
