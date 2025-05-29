```
next_transition_instant(zdt::ZonedDateTime) -> Union{ZonedDateTime, Nothing}
next_transition_instant(tz::TimeZone=localzone()) -> Union{ZonedDateTime, Nothing}
```

タイムゾーンの遷移が発生する次の瞬間を特定します（通常は夏時間のため）。将来の遷移が存在しない場合は `nothing` が返されます。

提供された `ZonedDateTime` は通常構築できないことに注意してください：

```julia
julia> instant = next_transition_instant(ZonedDateTime(2018, 3, 1, tz"Europe/London"))
2018-03-25T01:00:00+00:00

julia> instant - Millisecond(1)  # 変更前の瞬間
2018-03-25T00:59:59.999+00:00

julia> instant - Millisecond(0)  # 変更後の瞬間
2018-03-25T02:00:00+01:00

julia> ZonedDateTime(2018, 3, 25, 1, tz"Europe/London")  # `instant` を通常構築できない
ERROR: NonExistentTimeError: Local DateTime 2018-03-25T01:00:00 does not exist within Europe/London
...
```
