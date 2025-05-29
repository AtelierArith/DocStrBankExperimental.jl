```
Time(zdt::ZonedDateTime) -> Time
```

提供された `ZonedDateTime` の「ローカル時間」表現に基づいて `Time` を構築します。

参照: [`Time(::ZonedDateTime, ::Type{UTC})`](@ref)。

# 例

```jldoctest
julia> zdt = ZonedDateTime(2014, 5, 30, 21, tz"America/New_York")
2014-05-30T21:00:00-04:00

julia> Time(zdt)
21:00:00
```
