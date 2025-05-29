`BufferedInputStream{T}` は、タイプ `T` のソースからのバッファ付き読み取りを提供します。

`BufferedInputStream` にラップされた任意のタイプ `T` は、次のことを実装する必要があります：

```
BufferedStreams.readbytes!(source::T, buffer::Vector{UInt8}, from::Int, to::Int)
```

この関数は次のことを行うべきです：

  * `from` から始めて `to` を超えないように `buffer` を再充填する。
  * 読み取ったバイト数を返す。

バッファに新しいデータを読み込むことができなかった場合は、eof と解釈されます。
