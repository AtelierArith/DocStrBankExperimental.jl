```
upreferred(x::Number)
upreferred(x::Quantity)
```

Unit-convert `x` to units which are preferred for the dimensions of `x`. If you are using the factory defaults, this function will unit-convert to a product of powers of base SI units. If quantity `x` has [`Unitful.ContextUnits`](@ref)`(y,z)`, the resulting quantity will have units `ContextUnits(z,z)`.
