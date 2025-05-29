```
DateTime(zdt::ZonedDateTime, ::Type{UTC}) -> DateTime
```

提供された `ZonedDateTime` の UTC 表現に基づいて `DateTime` を構築します。

参照: [`DateTime(::ZonedDateTime)`](@ref)。

# 例

```jldoctest
julia> zdt = ZonedDateTime(2014, 5, 30, 21, tz"America/New_York")
2014-05-30T21:00:00-04:00

julia> DateTime(zdt, UTC)
2014-05-31T01:00:00
```
