```
FixValueFeedforward(
    component_type::Type{<:PSY.Component},
    source::Type{T},
    affected_values::Vector{DataType},
    meta = CONTAINER_KEY_EMPTY_META
) where {T}
```

別の問題からモデル内の変数またはパラメータの値を修正します。影響を受ける値としてパラメータまたは変数を使用できる唯一のフィードフォワードです。

# 引数:

  * `component_type::Type{<:PSY.Component}` : フィードフォワードを適用するコンポーネントのタイプを指定します
  * `source::Type{T}` : フィードフォワードの値のソースとして、VariableType、ParameterType、またはAuxVariableTypeを指定します
  * `affected_values::Vector{DataType}` : ソース値を使用して修正値が適用される変数を指定します
