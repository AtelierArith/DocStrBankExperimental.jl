```
GeneralizedStructDef(; is_mutable, header, lnn, fields, constructors)
```

構造体定義に一致します。プロパティ `.typename`、`.parameter`、および `.supertype` は `header` フィールドに転送されます。

# フィールド

  * `is_mutable::Bool`
  * `header::StructDefHeader`
  * `lnn::Union{LineNumberNode, NotProvided}` = not_provided
  * `fields::Vector{Tuple{TypedVar, LineNumberNode}}`
  * `constructors::Vector{Tuple{FuncDef, LineNumberNode}}`
