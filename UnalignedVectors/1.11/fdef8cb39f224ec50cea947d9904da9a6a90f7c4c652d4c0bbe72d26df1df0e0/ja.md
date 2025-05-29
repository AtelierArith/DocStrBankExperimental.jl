```
v = unaligned_reinterpret(T, a::Vector{UInt8})
```

`a`を`UnalignedVector{T}`として再解釈します。ただし、`T == UInt8`の場合は`a`が返されます。
