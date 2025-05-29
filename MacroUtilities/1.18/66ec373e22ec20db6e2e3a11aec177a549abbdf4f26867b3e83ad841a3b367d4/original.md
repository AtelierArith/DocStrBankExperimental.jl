```
copy_constructor(typename, fields::Vector{TypedVar}; [input_var::Symbol], [lnn::Union{LineNumberNode, Nothing}], [whereparams=not_provided], [copy_expr=default_copy_expr])
```

Returns a `FuncDef` copy constructor for `typename` with `fields`, i.e., a function of the form 

```julia
    $typename($input_var::$typename; field1::fieldtype1=Base.copy(getfield($input_var, :field1)), ...) = $typename(field1, ...)
```

Supports an optionally provided `lnn` and `whereparams`

`copy_expr(name, input_value)` must return an `Expr` that determines how the field `name` will be copied from `input_value` 
