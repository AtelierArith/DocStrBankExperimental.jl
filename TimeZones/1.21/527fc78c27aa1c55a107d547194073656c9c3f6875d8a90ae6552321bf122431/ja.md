```
DateTime(zdt::ZonedDateTime) -> DateTime
```

提供された `ZonedDateTime` の「ローカル時間」表現に基づいて `DateTime` を構築します。

!!! warning
    返された `DateTime` に対して行われる算術演算はタイムゾーンを考慮せず、操作がDSTの遷移を越える場合、正確なローカル時間を反映しません。


参照: [`DateTime(::ZonedDateTime, ::Type{UTC})`](@ref)。

# 例

```jldoctest
julia> zdt = ZonedDateTime(2014, 5, 30, 21, tz"America/New_York")
2014-05-30T21:00:00-04:00

julia> DateTime(zdt)
2014-05-30T21:00:00
```
