```
LiteralParameter(p)
```

A wrapper around a value `p` to indicate to [`new_derived_named_parameter`](@ref) or [`@convert_to_parameters`](@ref) to *not* convert the given parameter `p` into a named `@parameters` instance, but rather keep it as a numeric literal in the generated equations.
