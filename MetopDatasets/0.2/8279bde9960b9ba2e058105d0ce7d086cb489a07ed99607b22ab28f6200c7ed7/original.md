```
MetopVariable{T, N, R <: DataRecord} <: CommonDataModel.AbstractVariable{T, N}
```

`MetopVariable` wraps an `AbstractArray` so it can be used with `MetopDataset`.  The data array is normally `AbstractMetopDiskArray`.
