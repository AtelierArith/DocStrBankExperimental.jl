```
zip_encrypt_file!(zip::ZipArchive, index::Int, password::String; method::UInt16 = LIBZIP_EM_AES_128)
zip_encrypt_file!(zip::ZipArchive, filename::String, password::String; method::UInt16 = LIBZIP_EM_AES_128)
```

`zip` アーカイブ内の `index` の位置または `filename` にあるファイルの暗号化 `method` を `password` を使用して設定します。

[`encryption methods`](@ref encryption_methods) セクションも参照してください。
