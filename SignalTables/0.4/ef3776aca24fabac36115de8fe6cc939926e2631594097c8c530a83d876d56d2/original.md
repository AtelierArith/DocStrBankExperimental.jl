```
quantityType = quantity(numberType, numberUnit::Unitful.FreeUnits)
```

Returns Quantity from numberType and numberUnit, e.g. `quantity(Float64,u"m/s")`

# Example

```julia
using SignalTables
using Unitful

mutable struct Data{FloatType <: AbstractFloat}
    velocity::quantity(FloatType, u"m/s")
end

v = Data{Float64}(2.0u"mm/s")
@show v  # v = Data{Float64}(0.002 m s^-1)

sig = Vector{Union{Missing,quantity(Float64,u"m/s")}}(missing,3)
append!(sig, [1.0, 2.0, 3.0]u"m/s")
append!(sig, fill(missing, 2))
@show sig    # [missing, missing, missing, 1.0u"m/s", 2.0u"m/s", 3.0u"m/s", missing, missing]
```
