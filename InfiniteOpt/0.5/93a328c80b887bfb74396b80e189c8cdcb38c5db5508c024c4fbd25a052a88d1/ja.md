```
VariableData{V <: JuMP.AbstractVariable} <: AbstractDataObject
```

変数とそのデータを格納するための可変 `DataType`。

**フィールド**

  * `variable::V`: スカラー変数。
  * `name::String`: 印刷に使用される名前。
  * `lower_bound_index::Union{InfOptConstraintIndex, Nothing}`: 下限制約のインデックス。
  * `upper_bound_index::Union{InfOptConstraintIndex, Nothing}`: 上限制約のインデックス。
  * `fix_index::Union{InfOptConstraintIndex, Nothing}`: 固定制約のインデックス。
  * `zero_one_index::Union{InfOptConstraintIndex, Nothing}`: バイナリ制約のインデックス。
  * `integrality_index::Union{InfOptConstraintIndex, Nothing}`: 整数制約のインデックス。
  * `measure_indices::Vector{MeasureIndex}`: 従属測定のインデックス。
  * `constraint_indices::Vector{InfOptConstraintIndex}`: 従属制約のインデックス。
  * `in_objective::Bool`: これは目的に使用されていますか？
  * `point_var_indices::Vector{PointVariableIndex}`: 従属点変数のインデックス。
  * `semi_infinite_var_indices::Vector{SemiInfiniteVariableIndex}`: 従属半無限変数のインデックス。
  * `derivative_indices::Vector{DerivativeIndex}`: 従属導関数のインデックス。
  * `deriv_constr_indices::Vector{InfOptConstraintIndex}`: 従属導関数評価制約のインデックス。
