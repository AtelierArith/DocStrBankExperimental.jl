```
kwarg_constructor(typename, fields::Vector{TypedVar}, default_vals; [lnn::Union{LineNumberNode, Nothing)=nothing], [whereparams=not_provided])
```

Returns a `FuncDef` keyword argument constructor for `typename` with `fields` and `default_vals` is any collection that implements `Base.get(default_vals, fieldname, default)`
