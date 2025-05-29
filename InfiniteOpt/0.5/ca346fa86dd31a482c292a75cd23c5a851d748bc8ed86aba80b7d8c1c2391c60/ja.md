```
Measure{T <: JuMP.AbstractJuMPScalar, V <: AbstractMeasureData}
```

測定抽象のための `DataType` です。抽象は `data` によって決定され、測定が評価されるとき（消費されるとき）に `func` に適用されます。

**フィールド**

  * `func::T` 測定される `InfiniteOpt` 式。
  * `data::V` `AbstractMeasureData` の具体的なサブタイプで説明される抽象のデータ。
  * `object_nums::Vector{Int}`: 評価された測定式のパラメータオブジェクト番号（すなわち、`data` に属さない `func` のオブジェクト番号）。
  * `parameter_nums::Vector{Int}`: 評価された測定式をパラメータ化するパラメータ番号。（すなわち、`data` に属さない `func` のパラメータ番号）。
  * `constant_func::Bool`: `func` が `data` の無限パラメータによってパラメータ化されていないかどうかを示します。（すなわち、`func` と `data` のオブジェクト番号に交差がないか？）これは、可能であれば解析的評価を有効にするのに役立ちます。
