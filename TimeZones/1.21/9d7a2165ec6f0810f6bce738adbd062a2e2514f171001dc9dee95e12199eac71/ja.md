```
TimeZone(zdt::ZonedDateTime) -> TimeZone
```

`ZonedDateTime`に関連付けられた`TimeZone`を抽出します。

参照: [`timezone(::ZonedDateTime)`](@ref), [`FixedTimeZone(::ZonedDateTime)`](@ref).

# 例

```jldoctest
julia> zdt = ZonedDateTime(2014, 5, 30, 21, tz"America/New_York")
2014-05-30T21:00:00-04:00

julia> TimeZone(zdt)
America/New_York (UTC-5/UTC-4)
```
