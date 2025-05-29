```
zip_compress_file!(zip::ZipArchive, index::Int, method::Int = LIBZIP_CM_DEFAULT; compression_level::Int = 1)
zip_compress_file!(zip::ZipArchive, filename::String, method::Int = LIBZIP_CM_DEFAULT; compression_level::Int = 1)
```

`zip` アーカイブ内の位置 `index` または `filename` にあるファイルの圧縮 `method` を設定します。`compression_level` 引数は圧縮レベルを定義します。

詳細は [`Compression methods`](@ref compression_methods) セクションを参照してください。
