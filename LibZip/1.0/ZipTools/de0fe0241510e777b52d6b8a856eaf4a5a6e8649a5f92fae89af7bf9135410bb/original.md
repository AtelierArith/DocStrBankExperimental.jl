```
zip_compress_file!(zip::ZipArchive, index::Int, method::Int = LIBZIP_CM_DEFAULT; compression_level::Int = 1)
zip_compress_file!(zip::ZipArchive, filename::String, method::Int = LIBZIP_CM_DEFAULT; compression_level::Int = 1)
```

Set the compression `method` for the file at position `index` or by `filename` in the `zip` archive. The `compression_level` argument defines the compression level.

See also [`Compression methods`](@ref compression_methods) section.
