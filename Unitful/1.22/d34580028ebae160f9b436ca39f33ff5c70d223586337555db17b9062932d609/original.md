```
DimensionlessQuantity{T,U} = AbstractQuantity{T, NoDims, U}
```

Useful for dispatching on [`Unitful.Quantity`](@ref) types that may have units but no dimensions. (Units with differing power-of-ten prefixes are not canceled out.)

Example:

```jldoctest
julia> isa(1.0u"mV/V", DimensionlessQuantity)
true
```
