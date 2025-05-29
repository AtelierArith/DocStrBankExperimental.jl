```
today(tz::TimeZone) -> Date
```

指定された`TimeZone`で現在の`Date`を作成します。`Date(now(tz))`と同等です。

参照: [`now(::TimeZone)`](@ref), [`todayat(::TimeZone)`](@ref)。

# 例

```julia
julia> a, b = now(tz"Pacific/Midway"), now(tz"Pacific/Apia")
(2017-11-09T03:47:04.226-11:00, 2017-11-10T04:47:04.226+14:00)

julia> a - b
0 milliseconds

julia> today(tz"Pacific/Midway"), today(tz"Pacific/Apia")
(2017-11-09, 2017-11-10)
```
