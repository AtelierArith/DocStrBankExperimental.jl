```
ScalarParameterData{P <: ScalarParameter} <: AbstractDataObject
```

スカラーパラメータとそのデータを格納するための可変`DataType`です。

**フィールド**

  * `parameter::P`: スカラーパラメータ。
  * `object_num::Int`: `InfiniteModel.param_object_indices`内の対応する`ObjectIndex`の位置（`InfiniteModel.last_object_num`によって与えられます）。
  * `parameter_num::Int`: `InfiniteModel.last_param_num`によって与えられます（以前のパラメータが削除されると更新されます）。
  * `name::String`: 印刷に使用される名前。
  * `parameter_func_indices::Vector{ParameterFunctionIndex}`: 依存する無限パラメータ関数のインデックス。
  * `infinite_var_indices::Vector{InfiniteVariableIndex}`: 依存する無限変数のインデックス。
  * `derivative_indices::Vector{DerivativeIndex}`: 依存する導関数のインデックス。
  * `measure_indices::Vector{MeasureIndex}`: 依存する測定のインデックス。
  * `constraint_indices::Vector{InfOptConstraintIndex}`: 依存する制約のインデックス。
  * `in_objective::Bool`: これは目的に使用されていますか？これは有限パラメータに対してのみ真であるべきです。
  * `generative_measures::Vector{MeasureIndex}`: `parameter.generative_supp_info`を使用する測定のインデックス。
  * `has_internal_supports::Bool`: このパラメータには内部サポートがありますか？
  * `has_generative_supports::Bool`: 生成サポートが追加されましたか？
  * `has_deriv_constrs::Bool`: このパラメータに関連する無限モデルに導関数評価制約が追加されましたか？
