```
object = revert(transform, newobject, cache)
```

Revert the `transform` on the `newobject` using the `cache` from the corresponding [`apply`](@ref) call and return the original `object`. Only defined when the `transform` [`isrevertible`](@ref).
