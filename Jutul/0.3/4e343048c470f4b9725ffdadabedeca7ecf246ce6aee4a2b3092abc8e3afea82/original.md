```
si_unit(u::Union{String, Symbol})
```

Get the multiplicative SI unit conversion factor for a single unit. The return value is given so that `x*si_unit(:name)` will convert `x` to the SI representation of the unit with the given name.

# Examples

```jldoctest
julia> si_unit(:day) # Get days represented as seconds
86400.0
```
