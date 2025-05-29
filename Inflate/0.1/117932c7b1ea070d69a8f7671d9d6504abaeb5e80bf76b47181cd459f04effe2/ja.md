```
inflate_gzip(source::Vector{UInt8})
```

メモリ内の `source` を Gzip 圧縮形式で解凍します。出力も `Vector{UInt8}` になります。ストリーミングの対応物については、`InflateGzipStream` を参照してください。

```
gzip_headers = Dict{String, Any}()
inflate_gzip(source::Vector{UInt8}; headers = gzip_headers)
```

提供された `Dict` で gzip ヘッダーも取得します。

```
inflate_gzip(source::Vector{UInt8}; ignore_checksum = true)
```

整合性チェックのために、コンテンツおよびヘッダーの CRC 計算をスキップします。

参考: [RFC 1952](https://www.ietf.org/rfc/rfc1952.txt)
