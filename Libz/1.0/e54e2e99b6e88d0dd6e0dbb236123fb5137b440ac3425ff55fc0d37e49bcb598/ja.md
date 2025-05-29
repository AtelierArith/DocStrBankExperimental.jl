```
ZlibInflateInputStream(input[; <keyword arguments>])
```

gzip/zlibデータを解凍するためのzlibインフレート入力ストリームを構築します。

# 引数

  * `input`: 解凍する圧縮データを含むバイトベクター、IOオブジェクト、またはBufferedInputStream。
  * `bufsize::Integer=8192`: 入力および出力バッファサイズ。
  * `raw::Bool=falso`: trueの場合、データはzlibメタデータなしの生圧縮データです。
  * `gzip::Bool=true`: trueの場合、データはgzip圧縮されています。falseの場合、zlib圧縮されています。
  * `reset_on_end::Bool=true`: ストリームの終わりで、別のストリームの開始を見つけようとします。
