```
v = UnalignedVector{T}(a::Vector{UInt8})
```

Create a vector with element type `T` from a memory buffer of bytes (`UInt8`). In contrast with `reinterpret`, this allows array creation even if `a` does not have proper pointer alignment for `T`.
