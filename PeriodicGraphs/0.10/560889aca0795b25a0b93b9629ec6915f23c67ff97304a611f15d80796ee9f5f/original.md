```
reverse_hash_position(hash::Integer, n::Integer, ::Val{N}) where N
```

Given a `hash` obtained from [`hash_position`](@ref)`(x, n)` where `x` is a `PeriodicVertex{N}`, return the corresponding `x`.

If the offset of the returned `PeriodicVertex` is not needed, simply doing `mod1(x, n)` yields the identifier of the vertex and is faster.
