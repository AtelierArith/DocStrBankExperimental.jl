```
tensoradd!(C, A, pA, conjA, α=1, β=1 [, backend, allocator])
```

`C = β * C + α * permutedims(opA(A), pA)` を計算します。操作 `opA` は、`conjA` が `:N` の場合は `identity` として、`conjA` が `:C` の場合は `conj` として機能します。オプションで使用するバックエンド実装と、一時的なテンソルオブジェクトが必要な場合に使用されるアロケータを指定できます。

!!! warning
    順列は自明である必要があるか、`C` は `A` とエイリアスされてはいけません。


参照: [`tensoradd`](@ref).
