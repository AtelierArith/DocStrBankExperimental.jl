```
NumaAllocator(node)
```

クロスプラットフォームNUMAアロケータ

# 例

```jldoctest
julia> using NumaAllocators

julia> Array{UInt8}(NumaAllocator(0), 32, 32);
```
