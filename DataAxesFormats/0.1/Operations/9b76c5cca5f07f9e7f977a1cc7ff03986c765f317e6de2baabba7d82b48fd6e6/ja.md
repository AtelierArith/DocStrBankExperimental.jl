```
parse_float_dtype_value(
    operation_name::AbstractString,
    parameter_name::AbstractString,
    parameter_value::Token,
)::Maybe{Type}
```

[`parse_number_dtype_value`](@ref)と似ていますが、浮動小数点型のみを受け入れます。
