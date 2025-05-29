```
as_float(value)
```

Convert a number or string to a Float64 data type.

This is a useful helper for type conversions. Missing values are propagated.

# Arguments

  * `value`: An `AbstractString`, `Number`, or `missing` value.

# Examples

```jldoctest
julia> as_float(1)
1.0

julia> as_float("1.5")
1.5

julia> as_float(missing)
missing

julia> as_float("aa")
missing
```
