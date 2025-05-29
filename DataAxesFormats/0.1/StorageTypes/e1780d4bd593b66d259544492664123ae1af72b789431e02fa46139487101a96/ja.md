```
StorageScalarBase = Union{StorageReal, AbstractString}
```

`StorageScalar`である必要がある型を`where`句で使用するため。つまり、Juliaの型システムの制限のために、`where {T <: StorageScalarBase}`と書く代わりに`where {T <: StorageScalar}`と書きます。
