```
show_sexagesimal(x::Angle; base_unit::AngleUnits=°ᵃ)
```

Print an angle in units (u), minutes of unit (m), and seconds of unit (s) where unit is either degree (`°ᵃ`) or hour angle (`ʰ`). For degrees it is printed as `u° m′ s″` and for hour angle as `uʰ mᵐ sˢ`.

# Example

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles

julia> show_sexagesimal(20.2ua"°")
20° 11′ 59.99999999999746″

julia> show_sexagesimal(20.2ua"°"; base_unit = ua"ʰ")
1ʰ 20ᵐ 48.000000000000256ˢ
```
