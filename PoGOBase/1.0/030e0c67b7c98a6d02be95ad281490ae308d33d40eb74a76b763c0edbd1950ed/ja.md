```
only_pokemon(name::AbstractString; exact=false, equiv=false, kwargs...) → species
```

指定された名前に一致する`Species`オブジェクトを返し、一致するものが複数ある場合はエラーをスローします。

`exact`が`true`の場合、名前の完全一致のみが考慮されます。`equiv`が`true`の場合、すべての一致がそのタイプ、基本ステータス、および技において同等であればエラーはスローされません。

# 例

```jldoctest
julia> only_pokemon("scatterbug")
ERROR: multiple matching pokemon were found: ["SCATTERBUG", "SCATTERBUG_ARCHIPELAGO", "SCATTERBUG_CONTINENTAL", "SCATTERBUG_ELEGANT", "SCATTERBUG_FANCY", "SCATTERBUG_GARDEN", "SCATTERBUG_HIGH_PLAINS", "SCATTERBUG_ICY_SNOW", "SCATTERBUG_JUNGLE", "SCATTERBUG_MARINE", "SCATTERBUG_MEADOW", "SCATTERBUG_MODERN", "SCATTERBUG_MONSOON", "SCATTERBUG_OCEAN", "SCATTERBUG_POKEBALL", "SCATTERBUG_POLAR", "SCATTERBUG_RIVER", "SCATTERBUG_SANDSTORM", "SCATTERBUG_SAVANNA", "SCATTERBUG_SUN", "SCATTERBUG_TUNDRA"]

julia> only_pokemon("scatterbug"; equiv=true)
SCATTERBUG (BUG): (63, 63, 116); Fast: ["BUG_BITE_FAST", "TACKLE_FAST"]; Charged: ["STRUGGLE"]
```
