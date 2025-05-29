```
numa(node)
```

NUMAノード`node`に`NumaAllocator`を作成します。[`NumaAllocator`](@ref)コンストラクタの短縮形です。

# 例

```jldoctest
julia> using NumaAllocators

julia> Array{UInt8}(numa(0), 32, 32);
```
