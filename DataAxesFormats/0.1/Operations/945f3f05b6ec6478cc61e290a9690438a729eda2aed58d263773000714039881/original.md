```
parse_number_value(
    operation_name::AbstractString,
    parameter_name::AbstractString,
    parameter_value::Token,
    type::Type{T},
)::T where {T <: StorageReal}
```

Parse a numeric operation parameter.
