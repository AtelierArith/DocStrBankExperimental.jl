```
decompress!(
    ::Decompressor, out_data, in_data, [n_out::Integer]
)::Union{LibDeflateError, Int}
```

渡された `Decompressor` を使用して、`in_data` のデータを DEFLATE アルゴリズムを使用して `out_data` の最初のバイトに解凍し、出力に書き込まれたバイト数を返すか、`LibDeflateError` を返します。データは `out_data` に収まる必要があります。

解凍されたサイズが事前にわかっている場合は、それを `n_out` として渡してください。これによりパフォーマンスが向上しますが、間違っていると失敗します。
