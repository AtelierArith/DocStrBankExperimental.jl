Extends Unitful.jl to include Angle as an independent dimension in order to facilitate [dispatching](https://docs.julialang.org/en/v1/manual/methods/#Methods).

See the [Documentation](https://cmichelenstrofer.github.io/DimensionfulAngles/) for more information.

!!! note "Not SI"
    *Angle* is not an SI base dimension.


# Examples

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles

julia> 1.0ua"turn"
1.0 τ

julia> 1.0ua"rad" - 1.0ua"°"
0.9825467074800567 rad

julia> cos(45ua"°")
0.7071067811865476
```
