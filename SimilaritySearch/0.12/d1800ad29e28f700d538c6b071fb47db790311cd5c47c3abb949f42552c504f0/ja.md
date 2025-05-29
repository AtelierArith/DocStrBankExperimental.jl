```
DynamicMatrixDatabase(::Type{DType}, Dim::Integer)
```

空の `DynamicMatrixDatabase` を作成します。ここで `length(db[i]) == Dim` かつ `eltype(db[i]) == DType` です。
