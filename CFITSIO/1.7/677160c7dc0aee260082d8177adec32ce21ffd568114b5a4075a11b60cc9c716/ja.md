```
fits_create_diskfile(filename::AbstractString)
```

新しい空の出力 `FITSFile` を作成して開きます。 [`fits_create_file`](@ref) とは異なり、この関数は拡張ファイル名パーサーを使用せず、文字列をそのままファイル名として扱います。
