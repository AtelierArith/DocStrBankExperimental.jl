```
src, line1 = definition(String, method::Method)
```

Return a string with the code that defines `method`. Also return the first line of the definition, including the signature (which may not be the same line number returned by `whereis`). If the method can't be located (line number 0), then `definition` instead returns `nothing.`

Note this may not be terribly useful for methods that are defined inside `@eval` statements; see [`definition(Expr, method::Method)`](@ref) instead.

See also [`code_string`](@ref).
