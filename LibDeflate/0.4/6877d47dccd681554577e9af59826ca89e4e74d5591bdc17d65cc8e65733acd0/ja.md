```
parse_gzip_header(
    input, extra_data::Union{Vector{GzipExtraField}, Nothing}
)::Union{LibDeflateError, Tuple{UInt32, GzipHeader}}
```

入力データを解析し、`GzipHeader`オブジェクトまたは`LibDeflateError`を返します。パーサーは`max_len`バイト以上を読み取りません。gzipの追加データのベクターが渡された場合、新しいベクターを割り当てるのではなく、指定されたものを上書きします。
