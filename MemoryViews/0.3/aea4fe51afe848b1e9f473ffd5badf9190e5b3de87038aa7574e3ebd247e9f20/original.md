```
split_unaligned(v::T, ::Val{A}) -> Tuple{T, T} where {T <: MemoryView}
```

Split memory view `v` into two views `a` and `b`, `a` is the smallest prefix of `v` that gaurantees `b` is aligned to the integer value `A`. `A` must be a normal bit-integer, and a power of two in the range 1:64. If `v` is empty or already aligned, `a` will be empty. The element type of `v` must be a bitstype.

# Examples:

```
julia> split_unaligned(MemoryView(Int16[1, 2, 3]), Val(8))
(Int16[], Int16[1, 2, 3])

julia> split_unaligned(MemoryView(collect(0x01:0x20))[6:13], Val(8))
(UInt8[0x06, 0x07, 0x08], UInt8[0x09, 0x0a, 0x0b, 0x0c, 0x0d])
```
