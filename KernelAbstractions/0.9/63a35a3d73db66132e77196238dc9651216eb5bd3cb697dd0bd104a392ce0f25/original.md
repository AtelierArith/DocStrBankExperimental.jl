```
allocate(::Backend, Type, dims...)::AbstractArray
```

Allocate a storage array appropriate for the computational backend.

!!! note
    Backend implementations **must** implement `allocate(::NewBackend, T, dims::Tuple)`

