```
zip_add_dir!(zip::ZipArchive, dirname::String; flags::UInt32 = LIBZIP_FL_OVERWRITE)
```

`dirname`によって`zip`アーカイブにディレクトリを追加します。ディレクトリがまだ存在しない場合は作成され、存在する場合は上書きされます。

[`Add file flags`](@ref add_file_flags)セクションも参照してください。
