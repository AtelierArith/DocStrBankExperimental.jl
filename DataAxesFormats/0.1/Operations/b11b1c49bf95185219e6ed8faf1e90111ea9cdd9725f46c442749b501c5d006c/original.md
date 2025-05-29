```
parse_number_dtype_value(
    operation_name::AbstractString,
    parameter_name::AbstractString,
    parameter_value::Token,
)::Maybe{Type}
```

Parse the `dtype` operation parameter.

Valid names are `{B,b}ool`, `{UI,ui,I,i}nt{8,16,32,64}` and `{F,f}loat{32,64}`.
