```
ParameterFunctionData{F <: ParameterFunction} <: AbstractDataObject
```

`ParameterFunction`とそのデータを格納するための可変の`DataType`です。

**フィールド**

  * `func::F`: パラメータ関数。
  * `name::String`: 印刷に使用される名前。
  * `measure_indices::Vector{MeasureIndex}`: 従属測定のインデックス。
  * `constraint_indices::Vector{InfOptConstraintIndex}`: 従属制約のインデックス。
  * `semi_infinite_var_indices::Vector{SemiInfiniteVariableIndex}`: 従属半無限変数のインデックス。
  * `derivative_indices::Vector{DerivativeIndex}`: 従属導関数のインデックス。
