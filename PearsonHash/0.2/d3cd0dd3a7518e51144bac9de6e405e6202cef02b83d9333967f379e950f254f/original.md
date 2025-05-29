```
hashn!([T = UInt128], data::Vector{UInt8}; seed::UInt8 = 0)::T where T
```

Compute a (`8*n`)-bit hash for data where `n == sizeof(T)` (optionally specify `seed`). *Note:* `data` will be mutated in-place. See `hashn` for version without mutation.
