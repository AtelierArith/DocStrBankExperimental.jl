```
FixedTimeZone(zdt::ZonedDateTime) -> FixedTimeZone
```

`ZonedDateTime`によって提供されたタイムスタンプのUTCオフセットを使用して`FixedTimeZone`を構築します。`ZonedDateTime`で使用されるタイムゾーンが時間とともに変化するUTCオフセットを持つ場合、返される`FixedTimeZone`はタイムスタンプに基づいて変わります。

参照: [`TimeZone(::ZonedDateTime)`](@ref).

# 例

```jldoctest
julia> zdt1 = ZonedDateTime(2014, 5, 30, 21, tz"America/New_York")
2014-05-30T21:00:00-04:00

julia> FixedTimeZone(zdt1)
EDT (UTC-4)

julia> zdt2 = ZonedDateTime(2014, 2, 18, 6, tz"America/New_York")
2014-02-18T06:00:00-05:00

julia> FixedTimeZone(zdt2)
EST (UTC-5)
```
