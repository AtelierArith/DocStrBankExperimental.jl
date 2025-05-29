```
ustrip(x::Number)
ustrip(x::Quantity)
```

Returns the number out in front of any units. The value of `x` may differ from the number out front of the units in the case of dimensionless quantities, e.g. `1m/mm != 1`. See [`uconvert`](@ref) and the example below. Because the units are removed, information may be lost and this should be used with some care — see `ustrip(u,x)` for a safer alternative.

```jldoctest
julia> ustrip(2u"μm/m") == 2
true

julia> uconvert(NoUnits, 2u"μm/m") == 2//1000000
true
```
