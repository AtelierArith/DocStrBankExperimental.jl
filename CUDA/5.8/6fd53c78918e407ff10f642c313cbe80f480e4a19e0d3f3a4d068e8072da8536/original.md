```
current_context()
```

Returns the current context. Throws an undefined reference error if the current thread has no context bound to it, or if the bound context has been destroyed.

!!! warning
    This is a low-level API, returning the current context as known to the CUDA driver. For most users, it is recommended to use the [`context`](@ref) method instead.

