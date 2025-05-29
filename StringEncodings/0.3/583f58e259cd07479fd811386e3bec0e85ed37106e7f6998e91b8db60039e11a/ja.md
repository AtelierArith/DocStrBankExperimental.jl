```
decode([T,] a::AbstractVector{UInt8}, enc)
```

エンコーディング `enc` で表されるテキストのバイト配列 `a` を型 `T` の文字列に変換します。デフォルトでは、`String` が返されます。

非UTF-8エンコーディングのデータを持つ `s::String` を `decode` するには、`decode(codeunits(s), enc)` を使用して基になるバイト配列に作用させます。

`enc` は文字列または `Encoding` オブジェクトとして指定できます。入力データ `a` はバイトの `Vector{UInt8}`、その連続したサブアレイ、または `String`（またはその部分文字列）の `codeunits` であることができます。
