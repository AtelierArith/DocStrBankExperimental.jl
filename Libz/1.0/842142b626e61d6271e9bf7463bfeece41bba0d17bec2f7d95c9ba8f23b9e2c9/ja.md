```
ZlibInflateOutputStream(output[; <keyword arguments>])
```

gzip/zlibデータを解凍するためのzlibインフレート出力ストリームを構築します。

# 引数

  * `output`: 解凍されたデータを書き込むバイトベクター、IOオブジェクト、またはBufferedInputStream。
  * `bufsize::Integer=8192`: 入力および出力バッファサイズ。
  * `raw::Bool=false`: trueの場合、データはzlibメタデータなしの生圧縮データです。
  * `gzip::Bool=true`: trueの場合、データはgzip圧縮されています。falseの場合、zlib圧縮されています。
