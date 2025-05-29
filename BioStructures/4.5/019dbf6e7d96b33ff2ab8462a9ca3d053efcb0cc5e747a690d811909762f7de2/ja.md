```
writemultimmcif(filepath, cifs; gzip=false)
writemultimmcif(io, cifs; gzip=false)
```

複数の `MMCIFDict` を `Dict{String, MMCIFDict}` としてファイルパスまたはストリームに書き込みます。キーワード引数 `gzip`（デフォルトは `false`）は、出力がgzip圧縮されるかどうかを決定します。
