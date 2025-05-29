```
struct ZstdCodec <: Codec
ZstdCodec()
```

Zstandard圧縮はlibzstdを使用しています: www.zstd.net

Zstandardのフォーマットは[RFC8878](https://datatracker.ietf.org/doc/html/rfc8878)に文書化されています。

libzstdのシンプルなAPIのように、encodeはデータを保存された解凍サイズを持つ単一フレームとして圧縮します。解凍サイズが不明でもデコードは成功します。また、libzstdのシンプルなAPIのように、デコードは連結されたフレームを受け入れ、無効なデータが追加されている場合はエラーになります。

[`ZstdEncodeOptions`](@ref)および[`ZstdDecodeOptions`](@ref)も参照してください。
