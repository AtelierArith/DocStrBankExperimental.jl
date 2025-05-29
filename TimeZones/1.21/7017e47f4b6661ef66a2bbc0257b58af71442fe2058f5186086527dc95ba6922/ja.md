```
TimeZone(str::AbstractString, mask::Class) -> TimeZone
```

[`TimeZone(::AbstractString)`](@ref) と似ていますが、`mask` を使用して構築できるタイムゾーンクラスを制御できます。 "レガシー" として分類されるタイムゾーンを構築するために使用できます。

## 例

```jldoctest
julia> TimeZone("US/Pacific")
ERROR: ArgumentError: タイムゾーン "US/Pacific" はクラス `TimeZones.Class(:LEGACY)` に属しており、現在マスクによって許可されていません: `TimeZones.Class(:FIXED) | TimeZones.Class(:STANDARD)`

julia> TimeZone("US/Pacific", TimeZones.Class(:LEGACY))
US/Pacific (UTC-8/UTC-7)
```
