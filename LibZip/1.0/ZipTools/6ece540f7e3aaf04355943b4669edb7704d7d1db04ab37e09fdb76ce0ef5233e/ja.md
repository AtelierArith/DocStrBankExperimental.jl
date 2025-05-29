```
zip_open(path::String; flags::Int = LIBZIP_RDONLY) -> ZipArchive
```

指定された `flags` で `path` によって zip アーカイブファイルを開きます。

[`Open flags`](@ref open_flags) セクションも参照してください。
