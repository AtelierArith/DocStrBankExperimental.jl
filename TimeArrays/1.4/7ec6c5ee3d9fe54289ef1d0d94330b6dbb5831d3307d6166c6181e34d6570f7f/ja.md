```
TimeTick{T,V} <: AbstractTick{T,V}
```

型 `T<:TimeLike` のタイムスタンプと型 `V` の値を記述する型です。

## フィールド

  * `timestamp::T`: タイムスタンプ。
  * `value::V`: 値。

## アクセサ

  * `ta_timestamp(x::TimeTick)` -> `x.timestamp`
  * `ta_value(x::TimeTick)` -> `x.value`
