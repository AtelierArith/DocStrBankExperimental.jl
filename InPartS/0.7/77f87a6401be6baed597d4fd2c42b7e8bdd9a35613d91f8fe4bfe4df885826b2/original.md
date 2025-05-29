```
SimpleRegistrar{T<:Integer}(; next_id = one(T))
SimpleRegistrar() = SimpleRegistrar{UInt64}()
```

A simple registrar that returns sequential numbers of type `T` (defaults to `UInt64`) on calling [`set_id!`](@ref)/[`get_id!`](@ref) and does nothing else.
