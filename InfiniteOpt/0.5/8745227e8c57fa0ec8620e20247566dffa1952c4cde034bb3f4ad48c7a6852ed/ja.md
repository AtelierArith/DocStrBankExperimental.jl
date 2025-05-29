```
MultiParameterData{P <: DependentParameters} <: AbstractDataObject
```

[`DependentParameters`](@ref) とそのデータを格納するための可変 `DataType`。

**フィールド**

  * `parameters::P`: パラメータコレクション。
  * `object_num::Int`: `InfiniteModel.param_object_indices` における対応する `ObjectIndex` の位置（`InfiniteModel.last_object_num` によって与えられる）。
  * `parameter_nums::UnitRange{Int}`: `InfiniteModel.last_param_num` によって与えられる（以前のパラメータが削除されると更新される）。
  * `names::Vector{String}`: 各パラメータを印刷するために使用される名前。
  * `parameter_func_indices::Vector{ParameterFunctionIndex}`: 依存する無限パラメータ関数のインデックス。
  * `infinite_var_indices::Vector{InfiniteVariableIndex}`: 依存する無限変数のインデックス。
  * `derivative_indices::Vector{Vector{DerivativeIndex}}`: 依存する導関数のインデックス。
  * `measure_indices::Vector{Vector{MeasureIndex}}`: 依存する測定のインデックス。
  * `constraint_indices::Vector{Vector{InfOptConstraintIndex}}`: 依存する制約のインデックス。
  * `has_internal_supports::Bool`: このパラメータには内部サポートがありますか？
  * `has_deriv_constrs::Bool`: このパラメータに関連する無限モデルに導関数評価制約が追加されましたか？
