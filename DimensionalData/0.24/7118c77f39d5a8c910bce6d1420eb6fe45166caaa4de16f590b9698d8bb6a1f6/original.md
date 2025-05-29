```
rebuild(A::DimArray, data, dims, refdims, name, metadata) => DimArray
rebuild(A::DimArray; kw...) => DimArray
```

Rebuild a `DimArray` with new fields. Handling partial field update is dealt with in `rebuild` for `AbstractDimArray`.
