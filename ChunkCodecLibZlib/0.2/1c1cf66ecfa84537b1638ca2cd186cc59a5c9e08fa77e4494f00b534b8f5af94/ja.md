```
struct ZlibEncodeOptions <: EncodeOptions
ZlibEncodeOptions(; kwargs...)
```

libzlibを使用したzlib圧縮: https://www.zlib.net/

これはRFC 1950で説明されているzlibフォーマットです

# キーワード引数

  * `codec::ZlibCodec=ZlibCodec()`
  * `level::Integer=-1`: 圧縮レベルは-1または0から9の間でなければなりません。

    1は最高の速度を、9は最高の圧縮を、0はまったく圧縮しない（入力データは単にブロックごとにコピーされます）ことを意味します。-1は速度と圧縮の間のデフォルトの妥協を要求します（現在はレベル6に相当します）。
