```
NumaAllocators
```

特定のNUMAノードにメモリを割り当てるために`ArrayAllocators`を拡張します。

# 例

```julia
using NumaAllocators

Array{UInt8}(numa(0), 100)
Array{UInt8}(NumaAllocator(1), 100)
```
