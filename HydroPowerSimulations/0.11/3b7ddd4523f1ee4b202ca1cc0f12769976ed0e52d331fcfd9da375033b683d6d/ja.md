```
ReservoirLimitFeedforward(
    component_type::Type{<:PSY.Component},
    source::Type{T},
    affected_values::Vector{DataType},
    number_of_periods::Int,
    meta = CONTAINER_KEY_EMPTY_META
) where {T}
```

変数の合計をソース値に制限する制約を追加します。

# 引数:

  * `component_type::Type{<:`[`PowerSystems.Component`](@extref)`}` : Feedforwardを適用するコンポーネントのタイプを指定します
  * `source::Type{T}` : Feedforwardの値のソースとして、VariableType、ParameterType、またはAuxVariableTypeを指定します
  * `affected_values::Vector{DataType}` : ソース値を使用して貯水池制限が適用される変数を指定します
  * `number_of_periods::Int` : 制限が適用される合計期間数を指定します。たとえば、24ステップのシミュレーションで`number_of_periods = 24`の場合、貯水池制限が適用される24期間の合計に対して1つの制約のみが追加されます。`number_of_periods = 12`の場合、最初の12ステップと13:24ステップの2つの制約が作成されます。`number_of_periods`はシミュレーションステップの合計数を割り切る必要があります。
