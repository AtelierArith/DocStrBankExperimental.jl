```
sexagesimal(x::Angle; base_unit::AngleUnits=°ᵃ)
```

Convert an angle to the triple (unit, minutes of unit, seconds of unit), where unit is either degree (`°ᵃ`) or hour angle (`ʰᵃ`).

!!! note
    Minutes and seconds of a degree are different from minutes and seconds of an hour angle. In both cases a minute is 1/60ᵗʰ of the base unit and a second is 1/60ᵗʰ of that.


# Example

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles

julia> sexagesimal(20.2ua"°")
(20°, 11′, 59.99999999999746″)

julia> sexagesimal(20.2ua"°"; base_unit = ua"ʰ")
(1ʰ, 20ᵐ, 48.000000000000256ˢ)
```
