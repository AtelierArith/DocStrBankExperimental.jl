```
todayat(tod::Time, tz::TimeZone, [amb::Union{Integer,Bool}]) -> ZonedDateTime
```

指定された時刻の今日の`ZonedDateTime`を作成します。結果が指定された`TimeZone`内で曖昧な場合、曖昧さを解決するために`amb`を指定できます。

関連情報: [`now(::TimeZone)`](@ref), [`today(::TimeZone)`](@ref).

# 例

```julia
julia> today(tz"Europe/Warsaw")
2017-10-29

julia> todayat(Time(10, 30), tz"Europe/Warsaw")
2017-10-29T10:30:00+01:00

julia> todayat(Time(2), tz"Europe/Warsaw")
ERROR: AmbiguousTimeError: Local DateTime 2017-10-29T02:00:00 is ambiguous within Europe/Warsaw

julia> todayat(Time(2), tz"Europe/Warsaw", 1)
2017-10-29T02:00:00+02:00

julia> todayat(Time(2), tz"Europe/Warsaw", 2)
2017-10-29T02:00:00+01:00
```
