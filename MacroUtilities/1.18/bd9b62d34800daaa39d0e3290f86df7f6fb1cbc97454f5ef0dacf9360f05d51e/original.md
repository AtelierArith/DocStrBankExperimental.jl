```
StructDef(; is_mutable, header, lnn, fields, constructors)
```

Matches a struct definition. The properties `.typename`, `.parameter`, and `.supertype` forward to the `header` field.

# Fields

  * `is_mutable::Bool`
  * `header::StructDefHeader`
  * `lnn::Union{LineNumberNode, NotProvided}` = not_provided
  * `fields::Vector{Tuple{TypedVar, LineNumberNode}}`
  * `constructors::Vector{Tuple{FuncDef, LineNumberNode}}`
