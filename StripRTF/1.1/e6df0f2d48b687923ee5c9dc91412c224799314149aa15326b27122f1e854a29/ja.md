```
striprtf([out::IO,] text::AbstractString)
```

与えられた文字列 `text` が [リッチテキストフォーマット (RTF)](https://en.wikipedia.org/wiki/Rich_Text_Format) の場合、すべてのRTFフォーマットが削除された「プレーンテキスト」の文字列を返します。

オプションの `out` 引数が指定されている場合、出力はこの出力 `IO` ストリームに書き込まれ、`out` が返されます。
