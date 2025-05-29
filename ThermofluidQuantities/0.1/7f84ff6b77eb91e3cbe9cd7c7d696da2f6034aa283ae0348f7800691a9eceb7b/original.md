```
@displayedunits name unit dims
```

Set the preferred units for displaying quantities and create function `displayedunits` for returning these units and `ushow` for converting quantities into these units. The new unit type is specified with `name`, the default units with `unit`, and the dimensions with `dims`. The latter use the `Unitful` dimension names, `𝐌`, `𝐓`, `𝐋`, `𝚯`, in combinations

# Examples

```jldoctest myunit
julia> import ThermofluidQuantities: 𝐋, 𝐓

julia> @displayedunits MyVelocityType "m/s" 𝐋/𝐓

julia> MyVelocityType
Union{Unitful.Quantity{T,𝐋 𝐓⁻¹,U}, Unitful.Level{L,S,Unitful.Quantity{T,𝐋 𝐓⁻¹,U}} where S where L} where U where T
```
