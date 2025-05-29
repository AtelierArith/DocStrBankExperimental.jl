```
InflateGzipStream(stream::IO)
```

Gzip圧縮された`stream`のストリーミング解凍。メモリ内の対応物については、`inflate_gzip`を参照してください。

```
gzip_headers = Dict{String, Any}()
InflateGzipStream(stream::IO; headers = gzip_headers)
```

提供された`Dict`にgzipヘッダーも取得します。ヘッダーはオブジェクトが構築された直後に利用可能です。

```
InflateGzipStream(stream::IO; ignore_checksum = true)
```

整合性チェックのために、コンテンツおよびヘッダーのCRC計算をスキップします。

参考文献: [RFC 1952](https://www.ietf.org/rfc/rfc1952.txt)
