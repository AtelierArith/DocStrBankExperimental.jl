```
newobject = reapply(transform, object, cache)
```

Reapply the `transform` to (a possibly different) `object` using a `cache` that was created with a previous [`apply`](@ref) call. Fallback to [`apply`](@ref) without using the `cache`.
