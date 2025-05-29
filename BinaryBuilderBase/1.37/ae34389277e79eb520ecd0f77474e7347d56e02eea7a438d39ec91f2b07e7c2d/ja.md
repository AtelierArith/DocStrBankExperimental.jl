```
compress_dir(dir::AbstractString;
             compressor_stream = GzipCompressorStream,
             level::Int = 9,
             extension::AbstractString = ".gz",
             verbose::Bool = false)
```

指定された `compressor_stream` を使用して、圧縮レベルが `level` に等しい状態で `dir` 内のすべてのファイルを圧縮し、ファイル名に `extension` を追加します。最後に、元の非圧縮ファイルを削除します。
