```
TimeArray{T,V} <: AbstractTimeArray{T,V}
```

タイムスタンプの型 `T` と値の型 `V` を持つ時系列を記述する型です。

## フィールド

  * `values::Vector{TimeTick{T,V}}`: 時系列の要素。
  * `length::Int64`: 基になる配列の長さ。

## アクセサ

  * `ta_values(x::TimeArray)` -> `x.values`
