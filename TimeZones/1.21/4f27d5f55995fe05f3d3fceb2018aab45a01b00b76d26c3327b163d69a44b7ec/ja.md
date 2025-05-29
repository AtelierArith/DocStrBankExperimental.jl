```
Date(zdt::ZonedDateTime, ::Type{UTC}) -> Date
```

提供された `ZonedDateTime` の UTC 表現に基づいて `Date` を構築します。

参照: [`Date(::ZonedDateTime)`](@ref)。

# 例

```jldoctest
julia> zdt = ZonedDateTime(2014, 5, 30, 21, tz"America/New_York")
2014-05-30T21:00:00-04:00

julia> Date(zdt, UTC)
2014-05-31
```
