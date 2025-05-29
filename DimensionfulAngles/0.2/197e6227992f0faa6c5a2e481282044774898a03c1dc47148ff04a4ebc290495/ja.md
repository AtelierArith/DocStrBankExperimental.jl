```
show_sexagesimal(x::Angle; base_unit::AngleUnits=°ᵃ)
```

角度を単位 (u)、単位の分 (m)、単位の秒 (s) で表示します。単位は度 (`°ᵃ`) または時間角 (`ʰ`) のいずれかです。度の場合は `u° m′ s″` として表示され、時間角の場合は `uʰ mᵐ sˢ` として表示されます。

# 例

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles

julia> show_sexagesimal(20.2ua"°")
20° 11′ 59.99999999999746″

julia> show_sexagesimal(20.2ua"°"; base_unit = ua"ʰ")
1ʰ 20ᵐ 48.000000000000256ˢ
```
