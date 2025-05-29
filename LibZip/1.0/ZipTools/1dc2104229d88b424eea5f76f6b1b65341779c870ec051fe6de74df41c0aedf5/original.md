```
zip_encrypt_file!(zip::ZipArchive, index::Int, password::String; method::UInt16 = LIBZIP_EM_AES_128)
zip_encrypt_file!(zip::ZipArchive, filename::String, password::String; method::UInt16 = LIBZIP_EM_AES_128)
```

Set the encryption `method` for the file at position `index` or by `filename` in the `zip` archive using the `password`.

See also [`encryption methods`](@ref encryption_methods) section.
