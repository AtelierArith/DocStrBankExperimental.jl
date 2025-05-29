```
File{fmt}(filename)
```

Indicates that `filename` is a file of known [`DataFormat`](@ref) `fmt`. For example, `File{format"PNG"}(filename)` would indicate a PNG file.

!!! compat
    `File{fmt}(filename)` requires FileIO 1.6 or higher. The deprecated syntax `File(fmt, filename)` works on all FileIO 1.x releases.

