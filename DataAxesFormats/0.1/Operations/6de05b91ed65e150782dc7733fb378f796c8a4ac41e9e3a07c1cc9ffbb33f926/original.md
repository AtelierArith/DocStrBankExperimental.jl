```
parse_int_dtype_value(
    operation_name::AbstractString,
    parameter_name::AbstractString,
    parameter_value::Token,
)::Maybe{Type}
```

Similar to [`parse_number_dtype_value`](@ref), but only accept integer (signed or unsigned) types.
