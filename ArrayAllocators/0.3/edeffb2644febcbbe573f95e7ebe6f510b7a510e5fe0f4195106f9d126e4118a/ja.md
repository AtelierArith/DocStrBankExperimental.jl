```
malloc
```

[`MallocAllocator`](@ref) シングルトンインスタンス。`malloc` はメモリを割り当てるだけです。メモリを初期化せず、`undef` と同様に使用されます。詳細については、型と[C標準ライブラリ関数](https://en.cppreference.com/w/c/memory/malloc)を参照してください。

# 例

```jldoctest
julia> Array{UInt8}(malloc, 16, 16);

```
