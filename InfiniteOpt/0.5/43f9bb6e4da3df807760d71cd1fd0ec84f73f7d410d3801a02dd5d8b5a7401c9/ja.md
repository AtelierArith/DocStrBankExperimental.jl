```
MeasureData{M <: Measure} <: AbstractDataObject
```

可変の `DataType` で、[`Measure`](@ref)s とそのデータを格納します。

**フィールド**

  * `measure::M`: 測定構造。
  * `name::String`: `name(meas_expr d(par))` を印刷するために使用される基本名。
  * `measure_indices::Vector{MeasureIndex}`: 依存測定のインデックス。
  * `constraint_indices::Vector{InfOptConstraintIndex}`: 依存制約のインデックス。
  * `derivative_indices::Vector{DerivativeIndex}`: 依存導関数のインデックス。
  * `in_objective::Bool`: これは目的に使用されますか？
