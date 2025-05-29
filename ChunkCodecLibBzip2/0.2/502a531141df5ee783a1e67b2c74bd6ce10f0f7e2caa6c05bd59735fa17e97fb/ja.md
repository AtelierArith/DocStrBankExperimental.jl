```
struct BZ2Codec <: Codec
BZ2Codec()
```

libbzip2を使用したbzip2圧縮: https://sourceware.org/bzip2/

コマンドラインツール`bunzip2`のように、デコーディングは連結された圧縮データを受け入れ、デコンプレッションされたデータを連結して返します。`bunzip2`とは異なり、デコーディングは圧縮ストリームに無効なデータが追加されている場合にエラーになります。

[`BZ2EncodeOptions`](@ref)および[`BZ2DecodeOptions`](@ref)も参照してください。
