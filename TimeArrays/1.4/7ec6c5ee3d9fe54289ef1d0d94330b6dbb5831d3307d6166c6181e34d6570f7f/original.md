```
TimeTick{T,V} <: AbstractTick{T,V}
```

A type describing a timestamp of type `T<:TimeLike` and its value of type `V`.

## Fields

  * `timestamp::T`: The timestamp.
  * `value::V`: The value.

## Accessors

  * `ta_timestamp(x::TimeTick)` -> `x.timestamp`
  * `ta_value(x::TimeTick)` -> `x.value`
