```
FuncTransform(sig, world, fargs::Union{Vector{FuncArgs}, Nothing} = nothing;
    caller::Union{MethodInstance, Nothing} = nothing,
    method_tables::Union{Nothing, MethodTable} = nothing)
```

Constructs a `FuncTransform` object used to perform transformations on function `sig` of world age `world`.  `fargs` is used to specific the new function arguments of the new function. If `fargs` is `nothing`, the origin  arguments would be used. If `caller` is provided, it also set the backedge accordingly. The transformations  should be applied to `FuncTransform(...).fi::FuncInfo` and use `toCodeInfo` to get the result.
