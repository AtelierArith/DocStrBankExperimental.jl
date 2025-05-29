```
hashn([T = UInt128], data; seed::UInt8 = zero(UInt8))::T where T
```

Compute a (`8*n`)-bit hash for `Vector{UInt8}(data)` where `n == sizeof(T)` (optionally specify `seed`). *Note:* `data` is copied to prevent mutation (resulting in extra allocations).
