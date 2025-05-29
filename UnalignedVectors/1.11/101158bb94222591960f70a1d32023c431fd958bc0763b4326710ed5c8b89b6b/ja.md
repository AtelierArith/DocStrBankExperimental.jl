```
v = UnalignedVector{T}(a::Vector{UInt8})
```

バイト（`UInt8`）のメモリバッファから要素型 `T` のベクターを作成します。`reinterpret`とは異なり、`a` が `T` に対して適切なポインタのアライメントを持っていなくても配列を作成することができます。
