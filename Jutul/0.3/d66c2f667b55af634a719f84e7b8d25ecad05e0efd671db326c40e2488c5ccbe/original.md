```
convert_from_si(value, unit_name::Union{Symbol, String})
```

Convert `value` from SI representation to the unit in `unit_symbol`.

# Examples

```jldoctest
julia> convert_from_si(3600.0, :hour) # Get 3600 s represented as hours
1.0
```
