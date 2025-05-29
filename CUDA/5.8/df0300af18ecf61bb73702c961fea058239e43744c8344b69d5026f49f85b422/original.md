```
synchronize(ctx::Context)
```

Block for all the operations on `ctx` to complete. This is a heavyweight operation, typically you only need to call [`synchronize()`](@ref) which only synchronizes the stream associated with the current task.
