```
struct BZ2DecodeOptions <: DecodeOptions
BZ2DecodeOptions(; kwargs...)
```

libbzip2を使用したbzip2デコーディング: https://sourceware.org/bzip2/

コマンドラインツール`bunzip2`のように、デコーディングは連結された圧縮データを受け取り、デコンプレッションされたデータを連結して返します。`bunzip2`とは異なり、デコーディングは圧縮ストリームに無効なデータが追加されている場合にエラーを返します。

# キーワード引数

  * `codec::BZ2Codec=BZ2Codec()`
