```
unsafe_parse_gzip_header(
    in_ptr::Ptr, max_len::Integer,
    extra_data::Union{Vector{GzipExtraField}, Nothing}=nothing
)
```

入力データを解析し、`GzipHeader`オブジェクトまたは`LibDeflateError`を返します。パーサーは`max_len`バイト以上は読み込みません。gzipの追加データのベクターが渡された場合、新しいベクターを割り当てるのではなく、指定されたものを上書きします。
