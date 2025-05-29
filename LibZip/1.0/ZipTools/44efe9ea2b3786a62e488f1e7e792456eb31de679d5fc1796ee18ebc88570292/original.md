```
zip_add_dir!(zip::ZipArchive, dirname::String; flags::UInt32 = LIBZIP_FL_OVERWRITE)
```

Add a directory to a `zip` archive by the `dirname`, which will be created if it does not exist yet or overwritten if it does exist.

See also [`Add file flags`](@ref add_file_flags) section.
