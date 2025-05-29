```
inflate(source::Vector{UInt8})
```

メモリ内の `source` を、ラップされていない deflate 形式で解凍します。出力も `Vector{UInt8}` になります。ストリーミングの対応物については、`InflateStream` を参照してください。

参考: [RFC 1951](https://www.ietf.org/rfc/rfc1951.txt)
