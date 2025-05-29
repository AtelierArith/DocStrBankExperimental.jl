```
compress_dir(dir::AbstractString;
             compressor_stream = GzipCompressorStream,
             level::Int = 9,
             extension::AbstractString = ".gz",
             verbose::Bool = false)
```

Compress all files in `dir` using the specified `compressor_stream` with compression level equal to `level`, appending `extension` to the filenames. Remove the original uncompressed files at the end.
