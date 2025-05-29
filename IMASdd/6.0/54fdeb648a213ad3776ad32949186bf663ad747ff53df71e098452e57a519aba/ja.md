```
imas2h5i(
    @nospecialize(ids::Union{IDS,IDSvector}),
    filename::AbstractString;
    freeze::Bool=false,
    strict::Bool=false,
    run::Int=0,
    shot::Int=0,
    hdf5_backend_version::String="1.0",
    kw...
)
```

IMASプラットフォームによって生成されたHDF5ファイルにデータを保存します（すなわち、テンソル化されたHDF5）

# 引数

  * `kw...` 引数は `HDF5.h5open` 関数に渡されます
  * `freeze` は式を評価します
  * `strict` はITER IMASのみに厳密に存在するフィールドをダンプします
  * `run`、`shot`、`hdf5_backend_version` 引数はHDF5属性を設定するために使用されます
