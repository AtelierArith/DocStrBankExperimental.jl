```
split_unaligned(v::T, ::Val{A}) -> Tuple{T, T} where {T <: MemoryView}
```

メモリビュー `v` を二つのビュー `a` と `b` に分割します。`a` は `b` が整数値 `A` に整列することを保証する `v` の最小のプレフィックスです。`A` は通常のビット整数であり、1:64 の範囲の2の累乗でなければなりません。`v` が空であるか、すでに整列している場合、`a` は空になります。`v` の要素型はビット型でなければなりません。

# 例:

```
julia> split_unaligned(MemoryView(Int16[1, 2, 3]), Val(8))
(Int16[], Int16[1, 2, 3])

julia> split_unaligned(MemoryView(collect(0x01:0x20))[6:13], Val(8))
(UInt8[0x06, 0x07, 0x08], UInt8[0x09, 0x0a, 0x0b, 0x0c, 0x0d])
```
