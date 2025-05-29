```
with_context(f, [context]; kv...)
```

Run function `f` in the `context`. If extra `kv` pairs are provided, they will be merged with the `context` to form a new context. When `context` is not provided, the [`current_context`](@ref) will be used.
