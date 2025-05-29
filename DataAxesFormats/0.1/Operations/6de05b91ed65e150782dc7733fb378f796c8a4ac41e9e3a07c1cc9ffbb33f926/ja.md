```
parse_int_dtype_value(
    operation_name::AbstractString,
    parameter_name::AbstractString,
    parameter_value::Token,
)::Maybe{Type}
```

[`parse_number_dtype_value`](@ref)と似ていますが、整数（符号付きまたは符号なし）の型のみを受け入れます。
