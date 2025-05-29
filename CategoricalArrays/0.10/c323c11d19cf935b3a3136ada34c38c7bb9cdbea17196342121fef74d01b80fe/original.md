```
decompress(A::CategoricalArray)
```

Return a copy of categorical array `A` using the default reference type (UInt32). If `A` is using a small reference type (such as `UInt8` or `UInt16`) the decompressed array will have room for more levels.

To avoid the need to call decompress, ensure [`compress`](@ref) is not called when creating the categorical array.
