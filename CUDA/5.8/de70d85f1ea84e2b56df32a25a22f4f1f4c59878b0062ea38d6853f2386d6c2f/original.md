```
context()::CuContext
```

Get or create a CUDA context for the current thread (as opposed to `current_context` which may return `nothing` if there is no context bound to the current thread).
