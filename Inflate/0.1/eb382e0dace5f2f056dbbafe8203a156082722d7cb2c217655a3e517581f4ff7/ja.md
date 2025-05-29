```
InflateZlibStream(stream::IO)
```

Zlib圧縮された`stream`のストリーミング解凍。メモリ内の対応物については、`inflate_zlib`を参照してください。

```
InflateZlibStream(stream::IO; ignore_checksum = true)
```

整合性チェックのためにAdlerチェックサムの計算をスキップします。

参考: [RFC 1950](https://www.ietf.org/rfc/rfc1950.txt)
