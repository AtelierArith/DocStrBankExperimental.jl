```
inflate_zlib(source::Vector{UInt8})
```

メモリ内の `source` を Zlib 圧縮形式で解凍します。出力も `Vector{UInt8}` になります。ストリーミングの対応物については、`InflateZlibStream` を参照してください。

```
inflate_zlib(source::Vector{UInt8}; ignore_checksum = true)
```

整合性チェックのために Adler チェックサムの計算をスキップします。

参考文献: [RFC 1950](https://www.ietf.org/rfc/rfc1950.txt)
