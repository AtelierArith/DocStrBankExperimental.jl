```
struct Level{L, S, T<:Union{Real, AbstractQuantity{<:Real}}} <: LogScaled{L}
```

A logarithmic scale-based level. Details about the logarithmic scale are encoded in `L <: LogInfo`. `S` is a reference quantity for the level, not a type. This type has one field, `val::T`, and the log of the ratio `val/S` is taken. This type differs from [`Unitful.Gain`](@ref) in that `val` is a linear quantity.
