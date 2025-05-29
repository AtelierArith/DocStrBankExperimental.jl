```
read_dataset(parent::Union{File,Group}, name::AbstractString)
```

`parent` から名前 `name` のデータセットを読み込みます。通常、配列が返されます。データセットは開かれ、読み込まれ、閉じられます。

関連情報としては [`HDF5.open_dataset`](@ref)、[`Base.read`](@ref) を参照してください。
