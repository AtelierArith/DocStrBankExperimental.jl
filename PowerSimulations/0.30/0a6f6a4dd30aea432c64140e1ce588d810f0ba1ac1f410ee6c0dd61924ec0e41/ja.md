```
SemiContinuousFeedforward(
    component_type::Type{<:PSY.Component},
    source::Type{T},
    affected_values::Vector{DataType},
    meta = CONTAINER_KEY_EMPTY_META
) where {T}
```

指定された変数の下限を0.0に設定することを有効/無効にすることができます。通常、別の問題（通常はユニットコミットメント問題）で行われたコミットメント決定によって、経済的配分問題における`ActivePowerVariable`を制限するために使用されます。

# 引数:

  * `component_type::Type{<:PSY.Component}` : フィードフォワードが適用されるコンポーネントのタイプを指定します
  * `source::Type{T}` : フィードフォワードの値のソースとして、VariableType、ParameterType、またはAuxVariableTypeを指定します
  * `affected_values::Vector{DataType}` : ソース値を使用して半連続制限が適用される変数を指定します
