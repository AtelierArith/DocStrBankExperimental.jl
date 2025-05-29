```
v = unaligned_reinterpret(T, a::Vector{UInt8})
```

Reinterprets `a` as an `UnalignedVector{T}`, unless `T == UInt8` in which case `a` is returned.
