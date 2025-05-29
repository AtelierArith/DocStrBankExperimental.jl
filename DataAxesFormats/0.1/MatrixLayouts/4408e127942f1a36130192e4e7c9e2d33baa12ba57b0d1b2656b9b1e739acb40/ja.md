```
sparsify(matrix::AbstractMatrix{T}; copy::Bool = false)::AbstractMatrix{T} where {T <: StorageReal}
sparsify(vector::AbstractVector{T}; copy::Bool = false)::AbstractVector{T} where {T <: StorageReal}
```

配列のスパースバージョンを返します。これにより、行列のレイアウトが保持されます。`copy`が指定されている場合、すでにスパースであってもコピーが作成されます。
