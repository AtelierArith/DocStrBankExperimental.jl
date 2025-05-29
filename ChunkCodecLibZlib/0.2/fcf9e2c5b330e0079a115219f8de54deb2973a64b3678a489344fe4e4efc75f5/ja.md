```
struct GzipEncodeOptions <: EncodeOptions
GzipEncodeOptions(; kwargs...)
```

libzlibを使用したgzip圧縮: https://www.zlib.net/

これはRFC 1952で説明されているgzip (.gz)フォーマットです。

# キーワード引数

  * `codec::GzipCodec=GzipCodec()`
  * `level::Integer=-1`: 圧縮レベルは-1または0から9の間でなければなりません。

    1は最高の速度を、9は最高の圧縮を、0は全く圧縮しない（入力データは単にブロックごとにコピーされる）ことを意味します。-1は速度と圧縮の間のデフォルトの妥協を要求します（現在はレベル6に相当します）。
