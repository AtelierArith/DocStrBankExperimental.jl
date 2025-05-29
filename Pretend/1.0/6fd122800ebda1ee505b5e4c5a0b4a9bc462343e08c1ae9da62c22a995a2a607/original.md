```
called_at_least_once(f::Function, args...; kwargs...)
```

Return `true` if the function `f` with the provided `args` and `kwargs` was called at least once. This can be used after any executing a test script with mockable functions.
