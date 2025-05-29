```
as_integer(value)
```

Convert a number or string to an Int64 data type.

This is a useful helper for type conversions. Missing values are propagated. Any values after the decimal point are removed.

# Arguments

  * `value`: An `AbstractString`, `Number`, or `missing` value.

# Examples

```jldoctest
julia> as_integer(1)
1

julia> as_integer(1.5)
1

julia> as_integer("2")
2

julia> as_integer("2.5")
2

julia> as_integer(missing)
missing
```
