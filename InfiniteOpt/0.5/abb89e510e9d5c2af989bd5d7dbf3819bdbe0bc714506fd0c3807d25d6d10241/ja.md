```
ConstraintData{C <: JuMP.AbstractConstraint} <: AbstractDataObject
```

制約とそのデータを格納するための可変の `DataType`。

**フィールド**

  * `constraint::C`: 制約。
  * `object_nums::Vector{Int}`: 制約が依存するパラメータオブジェクトのオブジェクト番号。
  * `name::String`: 印刷に使用される名前。
  * `measure_indices::Vector{MeasureIndex}`: 依存する測定のインデックス。
  * `is_info_constraint::Bool`: これは変数情報に基づく制約ですか（例：下限）
