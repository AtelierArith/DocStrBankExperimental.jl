```
treehash(source_file::String; compressor::String = detect_compressor(source_file),
                              ignore_unstable_formats::Bool = false)
```

Treehash the archive given in `source_file`, automatically determining the compression type by inspecting the first few bytes.  Returns a vector of bytes.

If the compression type cannot be auto-determined, throws an error.

If `source_file` is a `.zip` file, throws an error unless `ignore_unstable_formats` is set to `true`.  Even then, it prints out a warning.
