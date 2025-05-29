```
ArrayAllocators
```

配列アロケータインターフェースと、`malloc`、`calloc`、およびメモリアライメントを使用した具体的な配列アロケータを定義します。

# 例

```julia
using ArrayAllocators

Array{UInt8}(malloc, 100)
Array{UInt8}(calloc, 1024, 1024)
Array{UInt8}(MemAlign(2^16), (1024, 1024, 16))
```

関連項目: `NumaAllocators`、`SafeByteCalculators`
