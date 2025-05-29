```
ZipArchive(data::Vector{UInt8}; flags::Int = LIBZIP_RDONLY) -> ZipArchive
ZipArchive(; flags::Int = LIBZIP_CREATE) -> ZipArchive
```

指定された `flags` を持つメモリ内バイトバッファから空の [`ZipArchive`](@ref) または既存のものを構築します。

詳細は [`Open flags`](@ref open_flags) セクションを参照してください。

## 例

```julia-repl
julia> ZipArchive(; flags = LIBZIP_CREATE | LIBZIP_CHECKCONS)
 ZipArchive:
    🔓 アーカイブはオープンで、使用する準備が整いました！
    📂 アーカイブは空です。
```

```julia-repl
julia> zip_file = read(".../secrets.zip");

julia> ZipArchive(zip_file)
 ZipArchive:
    🔓 アーカイブはオープンで、使用する準備が整いました！
    📁 アーカイブ内のファイル:
      📄 my_secret_1.txt/: 42 バイト
      [...]
```
