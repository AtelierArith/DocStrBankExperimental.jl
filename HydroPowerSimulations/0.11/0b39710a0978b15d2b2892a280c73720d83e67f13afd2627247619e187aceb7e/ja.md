```
ReservoirTargetFeedforward(
    component_type::Type{<:PowerSystems.Component},
    source::Type{T},
    affected_values::Vector{DataType},
    target_period::Int,
    penalty_cost::Float64,
    meta = CONTAINER_KEY_EMPTY_META
) where {T}
```

最小貯水池レベル目標を強制する制約を追加し、ペナルティ項に関連するスラック変数を持ちます。

# 引数:

  * `component_type::Type{<:`[`PowerSystems.Component`](@extref)`}` : Feedforwardを適用するコンポーネントのタイプを指定します
  * `source::Type{T}` : Feedforwardの値のソースとして、VariableType、ParameterType、またはAuxVariableTypeを指定します
  * `affected_values::Vector{DataType}` : ソース値を使用して貯水池目標が適用される変数を指定します
  * `target_period::Int` : 貯水池目標が適用される時間ステップを指定します。
  * `penalty_cost::Float64` : 希望する貯水池目標に達しなかった場合のペナルティコストを指定します。
