```
as_string(value)
```

Convert a number or string to a String data type.

This is a useful helper for type conversions. Missing values are propagated.

# Arguments

  * `value`: An `AbstractString`, `Number`, or `missing` value.

# Examples

```jldoctest
julia> as_string(1)
"1"

julia> as_string(1.5)
"1.5"

julia> as_string(missing)
missing
```
