```
UpperBoundFeedforward(
    component_type::Type{<:PSY.Component},
    source::Type{T},
    affected_values::Vector{DataType},
    add_slacks::Bool = false,
    meta = CONTAINER_KEY_EMPTY_META
) where {T}
```

他のモデルからのフィードフォワードを実装するためのパラメータ化された上限制約を構築します。

# 引数:

  * `component_type::Type{<:PSY.Component}` : フィードフォワードを適用するコンポーネントのタイプを指定します
  * `source::Type{T}` : フィードフォワードの値のソースとして、VariableType、ParameterType、またはAuxVariableTypeを指定します
  * `affected_values::Vector{DataType}` : ソース値を使用して上限が適用される変数を指定します
  * `add_slacks::Bool = false` : 上限制約を緩和するためにスラック変数を追加します。
