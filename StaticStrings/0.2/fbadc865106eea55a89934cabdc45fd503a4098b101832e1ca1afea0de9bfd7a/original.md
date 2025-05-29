```
SubStaticString(data::NTuple{N, UInt8}, ind::Integer)
SubStaticString(data::NTuple{N, UInt8}, ind::AbstractUnitRange)
substatic"string"N
```

[`AbstractStaticString`](@ref) that stores up to `N` codeunits in a NTuple{N,UInt8}. The actual codeunits used are a subset indicated by an AbstractUnitRange.
