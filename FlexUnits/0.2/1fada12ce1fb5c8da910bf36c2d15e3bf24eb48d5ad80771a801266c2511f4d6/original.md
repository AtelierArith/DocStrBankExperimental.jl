```
NoDims{P}
```

A unitless dimension, compatible with any other dimension

Calling `getproperty` will always return `zero(P)` promote(Type{<:NoDims}, D<:AbstractDimension) will return D  convert(Type{D}, NoDims) where D<:AbstractDimensions will return D()
