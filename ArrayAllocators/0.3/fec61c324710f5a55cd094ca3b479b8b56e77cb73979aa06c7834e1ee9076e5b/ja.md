```
calloc
```

[`CallocAllocator`](@ref) シングルトンインスタンス。`calloc` はメモリを割り当て、初期化を `0` に保証します。詳細については型を参照し、さらなる詳細については [C標準ライブラリ関数](https://en.cppreference.com/w/c/memory/calloc) を参照してください。

# 例

```jldoctest
julia> A = Array{UInt8}(calloc, 16, 16);

julia> sum(A)
0x0000000000000000
```
