```
ZonedDateTime(str::AbstractString)
```

`str`を解析することによって`ZonedDateTime`を構築します。このメソッドは、`zdt == ZonedDateTime(string(zdt))`が成り立つように設計されており、ここで`zdt`は任意の`ZonedDateTime`オブジェクトです。このメソッドは常に`FixedTimeZone`を持つ`ZonedDateTime`を作成するため、日付/時刻の算術演算で異なる結果が得られる可能性があることに注意してください。

## 例

```jltest
julia> zdt = ZonedDateTime(2025, 3, 8, 9, tz"America/New_York")
2025-03-08T09:00:00-05:00

julia> timezone(zdt)
America/New_York (UTC-5/UTC-4)

julia> zdt + Day(1)
2025-03-09T09:00:00-04:00

julia> pzdt = ZonedDateTime(string(zdt))
2025-03-08T09:00:00-05:00

julia> timezone(pzdt)
UTC-05:00

julia> pzdt + Day(1)
2025-03-09T09:00:00-05:00
```
