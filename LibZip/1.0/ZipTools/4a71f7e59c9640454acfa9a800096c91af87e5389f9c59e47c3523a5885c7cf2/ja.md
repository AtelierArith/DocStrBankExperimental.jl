```
zip_get_file_info(zip::ZipArchive, filename::String; flags::UInt32 = LIBZIP_FL_ENC_GUESS)
zip_get_file_info(zip::ZipArchive, index::Int; flags::UInt32 = LIBZIP_FL_ENC_GUESS)
```

`zip` アーカイブ内の `filename` に関する情報を返します。

[`File info flags`](@ref file_info_flags) セクションも参照してください。
