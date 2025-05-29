```
unsafe_gzip_compress!(
    compressor::Compressor,
    out_ptr::Ptr, out_len::Integer,
    in_ptr::Ptr, in_len::Integer,
    comment::Union{Nothing, ReadableMemory},
    filename::Union{Nothing, ReadableMemory},
    extra::Union{Nothing, ReadableMemory},
    header_crc::Bool
)::Union{LibDeflateError, Int}
```

`Compressor`を使用して、`in_ptr`から`in_len`バイト分の入力をgzip圧縮し、`out_ptr`に出力します。結果として得られるgzipデータが`out_len`を超える可能性がある場合は、エラーを返します。オプションで、gzipコメント、ファイル名、または追加データを含めることができます。これらは適用できない場合はすべて`nothing`でなければなりません。

オプションのデータ`comment`、`filename`、`extra`を追加します。

  * `comment`と`filename`にはバイト`0x00`を含めてはいけません。
  * `extra`は最大で`typemax(UInt16)`バイトの長さでなければなりません。

`out_ptr`に書き込まれたバイト数を返します。

参照: [`gzip_compress!`](@ref)
