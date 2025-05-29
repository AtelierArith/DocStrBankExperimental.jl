```
θ₀
```

A quantity equal to the central angle of a plane circular sector whose arc length is equal to that of its radius. It has a value of exactly 1 rad or approximately 57.2958°. Used as the defining constant of Angle dimension in several proposed SI extension systems.

Dimensions: 𝐀.

See also [`DimensionfulAngles.radᵃ`](@ref).

# Examples

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles

julia> θ₀
1//1 rad

julia> θ₀ |> ua"°"
57.29577951308232°

julia> 2.1ua"rad" / θ₀
2.1
```
