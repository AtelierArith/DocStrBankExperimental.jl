```
compress!(::Compressor, out_data, in_data)::Union{LibDeflateError, Int}
```

渡された `Compressor` を使用して、DEFLATE アルゴリズムを使用して `in_data` を `out_data` の最初のバイトに圧縮します。データは `out_data` に収まる必要があります。

出力に書き込まれたバイト数、または `LibDeflateError` を返します。
