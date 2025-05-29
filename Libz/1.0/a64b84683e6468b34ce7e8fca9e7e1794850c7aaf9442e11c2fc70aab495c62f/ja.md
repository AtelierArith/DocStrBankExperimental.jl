```
ZlibDeflateInputStream(input[; <keyword arguments>])
```

gzip/zlibデータを圧縮するためのzlib deflate入力ストリームを構築します。

# 引数

  * `input`: 圧縮するデータを含むバイトベクター、IOオブジェクト、またはBufferedInputStream。
  * `bufsize::Integer=8192`: 入力および出力バッファサイズ。
  * `raw::Bool=false`: trueの場合、データはzlibメタデータなしの生圧縮データです。
  * `gzip::Bool=true`: trueの場合、データはgzip圧縮されています。falseの場合、zlib圧縮されています。
  * `level::Integer=6`: 1-9の圧縮レベル。
  * `mem_level::Integer=8`: 1-9の圧縮に使用するメモリ。
  * `strategy=Z_DEFAULT_STRATEGY`: 圧縮戦略; zlibのドキュメントを参照してください。
