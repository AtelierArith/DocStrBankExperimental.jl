```
unsafe_gzip_decompress!(
    ::Decompressor, out_data::Vector{UInt8},
    max_outlen::Integer, in_ptr::Ptr, len::Integer,
    extra_data::Union{Vector{GzipExtraField}, Nothing}
)::Union{LibDeflateError, GzipDecompressResult}
```

`Decompressor`を使用して、`in_ptr`のgzipデータを`len`バイト分`out_data`にデコンプレッションします。`out_data`に十分なスペースがない場合は、`out_data`のサイズを変更しますが、`max_outlen`を超える場合はエラーを返します。`extra_data`が`nothing`でない場合は、ベクターを再利用して上書きします。

`GzipDecompressResult`を返します。

参照: [`gzip_decompress!`](@ref)
