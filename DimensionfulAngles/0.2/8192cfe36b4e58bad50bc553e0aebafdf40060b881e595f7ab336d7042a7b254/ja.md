```
sexagesimal(x::Angle; base_unit::AngleUnits=°ᵃ)
```

角度を三つ組 (単位、単位の分、単位の秒) に変換します。単位は度 (`°ᵃ`) または時間角 (`ʰᵃ`) のいずれかです。

!!! note
    度の分と秒は、時間角の分と秒とは異なります。どちらの場合も、分は基準単位の1/60ᵗʰであり、秒はその1/60ᵗʰです。


# 例

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles

julia> sexagesimal(20.2ua"°")
(20°, 11′, 59.99999999999746″)

julia> sexagesimal(20.2ua"°"; base_unit = ua"ʰ")
(1ʰ, 20ᵐ, 48.000000000000256ˢ)
```
