```
File{fmt}(filename)
```

は、`filename` が既知の [`DataFormat`](@ref) `fmt` のファイルであることを示します。例えば、`File{format"PNG"}(filename)` は PNG ファイルを示します。

!!! compat
    `File{fmt}(filename)` は FileIO 1.6 以上が必要です。非推奨の構文 `File(fmt, filename)` はすべての FileIO 1.x リリースで動作します。

