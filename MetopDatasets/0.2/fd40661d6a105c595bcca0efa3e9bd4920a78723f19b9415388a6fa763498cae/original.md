```
MetopDiskArray{T, N} <: AbstractMetopDiskArray{T, N}
```

Struct to handle  lazy loading of a variable in a Metop product. The raw types in the product is mapped without any  scaling. Auto conversion can be enabled for `RecordSubType` e.g. converting `VInteger` to `Float64`.
