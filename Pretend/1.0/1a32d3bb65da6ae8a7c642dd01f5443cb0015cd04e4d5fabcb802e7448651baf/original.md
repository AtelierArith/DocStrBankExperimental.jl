```
was_not_called(f::Function, args...; kwargs...)
```

Return `true` if the function `f` with the provided `args` and `kwargs` was not called at all. This can be used after any executing a test script with mockable functions.
