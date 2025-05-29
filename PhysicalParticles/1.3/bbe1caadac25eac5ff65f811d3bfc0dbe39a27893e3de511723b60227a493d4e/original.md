```
ZeroValue(::Type{T}, ::Nothing) where T<:Number
ZeroValue(::Type{T}, units::Vector{Unitful.FreeUnits{N, D, nothing} where D where N} = uAstro) where T<:Number
```

Construct an immutable struct providing zero values of type `T` in corresponding `units` (default is `uAstro`). Use `nothing` if unitless. Useful for accumulated summation, array initialization, etc.

# Examples

```jl
ZeroValue(Float32, nothing)
ZeroValue(Int32)
ZeroValue(BigFloat, uSI)
ZeroValue(Measurement, uCGS)
```
