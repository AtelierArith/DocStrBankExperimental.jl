```
readmultimmcif(filepath; gzip=false)
readmultimmcif(io; gzip=false)
```

複数の `MMCIFDict` をファイルパスまたはストリームから読み込みます。返される `Dict{String, MMCIFDict}` の各 `MMCIFDict` は、入力の mmCIF データブロックに対応しています。このようなファイルの例は、Protein Data Bank の化学成分辞書です。キーワード引数 `gzip`（デフォルトは `false`）は、入力が gzipped かどうかを決定します。
