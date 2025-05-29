```
octet(g::ECGroup; mode = :uncompressed|:hybrid|:compressed)::Vector{UInt8}
```

楕円曲線ポイントをFIPS 186-4標準で指定されたオクテット表現に変換します。 `mode=:uncompressed|:hybrid|:compressed`を使用して圧縮モードを指定できます。

`iscompressable`も参照してください。
