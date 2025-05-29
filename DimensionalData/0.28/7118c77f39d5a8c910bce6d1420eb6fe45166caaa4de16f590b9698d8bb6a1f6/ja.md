```
rebuild(A::DimArray, data, dims, refdims, name, metadata) => DimArray
rebuild(A::DimArray; kw...) => DimArray
```

新しいフィールドで `DimArray` を再構築します。部分的なフィールドの更新は、`AbstractDimArray` の `rebuild` で処理されます。
