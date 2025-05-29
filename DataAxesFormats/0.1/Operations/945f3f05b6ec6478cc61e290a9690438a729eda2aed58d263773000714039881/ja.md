```
parse_number_value(
    operation_name::AbstractString,
    parameter_name::AbstractString,
    parameter_value::Token,
    type::Type{T},
)::T where {T <: StorageReal}
```

数値操作パラメータを解析します。
