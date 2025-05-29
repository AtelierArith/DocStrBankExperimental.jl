```
Inflate
```

Pure Julia implementation of decompression of the Deflate format and the Zlib and Gzip wrapper formats.

In-memory decompression is done by the following functions:

|                            function | decompresses |
| -----------------------------------:| ------------:|
|      `inflate(data::Vector{UInt8})` | Deflate data |
| `inflate_zlib(data::Vector{UInt8})` |    Zlib data |
| `inflate_gzip(data::Vector{UInt8})` |    Gzip data |

Streaming decompression is done using the following types:

|                          stream |   decompresses |
| -------------------------------:| --------------:|
|     `InflateStream(stream::IO)` | Deflate stream |
| `InflateZlibStream(stream::IO)` |    Zlib stream |
| `InflateGzipStream(stream::IO)` |    Gzip stream |
