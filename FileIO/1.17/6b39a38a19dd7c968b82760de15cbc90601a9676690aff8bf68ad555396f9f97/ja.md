```
Stream{fmt}(io, filename=nothing)
```

ストリーム `io` が既知のフォーマット [`DataFormat`](@ref) `fmt` で書き込まれていることを示します。例えば、`Stream{format"PNG"}(io)` はPNGフォーマットを示します。既知であれば、オプションの `filename` 引数を使用してエラーメッセージなどを改善できます。

!!! compat
    `Stream{fmt}(io, ...)` はFileIO 1.6以上が必要です。非推奨の構文 `Stream(fmt, io, ...)` はすべてのFileIO 1.xリリースで動作します。

