```
get_backend(A::AbstractArray)::Backend
```

Get a [`Backend`](@ref) instance suitable for array `A`.

!!! note
    Backend implementations **must** provide `get_backend` for their custom array type. It should be the same as the return type of [`allocate`](@ref)

