```
densify(matrix::AbstractMatrix{T}; copy::Bool = false)::AbstractMatrix{T} where {T <: StorageReal}
densify(vector::AbstractVector{T}; copy::Bool = false)::AbstractVector{T} where {T <: StorageReal}
```

配列の密なバージョンを返します。これにより、行列のレイアウトが保持されます。`copy`が指定されている場合、すでに密であってもコピーが作成されます。
