```
インフレート
```

Deflate形式およびZlibとGzipラッパー形式のデコンプレッションの純粋なJulia実装。

メモリ内デコンプレッションは、以下の関数によって行われます：

|                                  関数 | デコンプレッションするデータ |
| -----------------------------------:| --------------:|
|      `inflate(data::Vector{UInt8})` |     Deflateデータ |
| `inflate_zlib(data::Vector{UInt8})` |        Zlibデータ |
| `inflate_gzip(data::Vector{UInt8})` |        Gzipデータ |

ストリーミングデコンプレッションは、以下の型を使用して行われます：

|                           ストリーム | デコンプレッションするデータ |
| -------------------------------:| --------------:|
|     `InflateStream(stream::IO)` |   Deflateストリーム |
| `InflateZlibStream(stream::IO)` |      Zlibストリーム |
| `InflateGzipStream(stream::IO)` |      Gzipストリーム |
