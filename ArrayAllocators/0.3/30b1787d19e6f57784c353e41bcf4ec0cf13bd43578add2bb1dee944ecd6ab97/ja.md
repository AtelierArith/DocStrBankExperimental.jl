```
AbstractArrayAllocator{B}
```

配列アロケータの親抽象型。パラメータ `B` は AbstractByteCalculator です。`Array{T}(allocator, dims...) where T = Array{T}(allocator, dims)` を定義します。
