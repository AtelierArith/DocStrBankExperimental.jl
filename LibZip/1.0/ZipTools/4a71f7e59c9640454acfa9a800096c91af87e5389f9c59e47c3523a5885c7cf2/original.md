```
zip_get_file_info(zip::ZipArchive, filename::String; flags::UInt32 = LIBZIP_FL_ENC_GUESS)
zip_get_file_info(zip::ZipArchive, index::Int; flags::UInt32 = LIBZIP_FL_ENC_GUESS)
```

Return information about the `filename` in a `zip` archive.

See also [`File info flags`](@ref file_info_flags) section.
