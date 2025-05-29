```
gzip_compress!(
    compressor::Compressor,
    output::Vector{UInt8},
    input::ReadableMemory
    comment=nothing,
    filename=nothing,
    extra=nothing,
    header_crc::Bool=false
)::Union{LibDeflateError, Vector{UInt8}}
```

Gzipは`input`を`output`に圧縮し、出力をフィットするようにサイズ変更します。`output`を返します。

オプションのデータ`comment`、`filename`、`extra`を追加します。これらは適用できない場合はすべて`nothing`でなければなりません。

  * `comment`と`filename`はバイト`0x00`を含んではいけません。
  * `extra`は最大で`typemax(UInt16)`バイトの長さでなければなりません。

`header_crc`がtrueの場合、ヘッダーCRCチェックサムを追加します。

参照: [`unsafe_gzip_compress!`](@ref)
