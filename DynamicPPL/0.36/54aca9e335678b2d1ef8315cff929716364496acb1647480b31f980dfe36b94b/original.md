```
PrefixContext(vn::VarName[, context::AbstractContext])
PrefixContext(vn::Val{sym}[, context::AbstractContext]) where {sym}
```

Create a context that allows you to use the wrapped `context` when running the model and prefixes all parameters with the VarName `vn`.

`PrefixContext(Val(:a), context)` is equivalent to `PrefixContext(@varname(a), context)`. If `context` is not provided, it defaults to `DefaultContext()`.

This context is useful in nested models to ensure that the names of the parameters are unique.

See also: [`to_submodel`](@ref)
