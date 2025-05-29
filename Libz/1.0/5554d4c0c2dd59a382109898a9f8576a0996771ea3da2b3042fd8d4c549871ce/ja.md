```
ZlibDeflateOutputStream(output[; <keyword arguments>])
```

gzip/zlibデータを圧縮するためのzlib deflate出力ストリームを構築します。

# 引数

  * `output`: 圧縮データを書き込むバイトベクター、IOオブジェクト、またはBufferedInputStream。
  * `bufsize::Integer=8192`: 入力および出力バッファサイズ。
  * `raw::Bool=false`: trueの場合、データはzlibメタデータなしの生圧縮データです。
  * `gzip::Bool=true`: trueの場合、データはgzip圧縮されています。falseの場合、zlib圧縮されています。
  * `level::Integer=6`: 圧縮レベル（1-9）。
  * `mem_level::Integer=8`: 圧縮に使用するメモリ（1-9）。
  * `strategy=Z_DEFAULT_STRATEGY`: 圧縮戦略。zlibのドキュメントを参照してください。
