```
parse_number_dtype_value(
    operation_name::AbstractString,
    parameter_name::AbstractString,
    parameter_value::Token,
)::Maybe{Type}
```

`dtype` 操作パラメータを解析します。

有効な名前は `{B,b}ool`、`{UI,ui,I,i}nt{8,16,32,64}` および `{F,f}loat{32,64}` です。
