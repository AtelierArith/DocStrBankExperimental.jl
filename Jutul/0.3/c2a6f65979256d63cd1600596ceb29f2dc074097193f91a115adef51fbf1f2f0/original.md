```
convert_to_si(value, unit_name::String)
```

Convert `value` to SI representation from value in the unit given by `unit_symbol`.

# Examples

```jldoctest
julia> convert_to_si(1.0, :hour) # Get 1 hour represented as seconds
3600.0
```
