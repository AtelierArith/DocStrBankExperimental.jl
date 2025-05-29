```
tensortrace!(C, A, p, q, conjA, α=1, β=0 [, backend, allocator])
```

`C = β * C + α * permutedims(opA(A), (p, q))` を計算します。ここで、`A` は部分的にトレースされており、`q[1]` のインデックスが `q[2]` のインデックスと収束し、他のインデックスは `p` に従って置換されます。操作 `opA` は、`conjA` が `false` の場合は `identity` として、`conjA` が `true` の場合は `conj` として機能します。オプションで使用するバックエンド実装と、一時的なテンソルオブジェクトが必要な場合に使用されるアロケータを指定できます。

!!! warning
    オブジェクト `C` は `A` とエイリアスされてはいけません。


参照: [`tensortrace`](@ref). ```
