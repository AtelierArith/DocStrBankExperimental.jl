```
omit_fields(x, fields::Symbol...)
omit_fields(x, fields::NTuple{<:Any, Symbol})
omit_fields(fields::Symbol...)
omit_fields(fields::NTuple{<:Any, Symbol})
```

Return an object excluding `fields` from the fields of `x`, as per `getfield`. Curried versions exist, which return a function for selecting the given fields.

This function differs from returning a named tuple of fields (e.g. `x -> (;x.a, x.b)`) in that it does not narrow the types of the returned fields. A field of type `Any` of `x` is a field of type `Any` in the returned value. This ensures that pick*fields can be safely used with `hoist*type`of [`Transformer`](@ref).
