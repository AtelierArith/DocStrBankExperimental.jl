```
MMCIFDict(filepath; gzip=false)
MMCIFDict(io; gzip=false)
MMCIFDict()
```

マクロ分子結晶学情報ファイル（mmCIF）辞書。

標準の `Dict` に似た関数を使用してアクセスできます。キーは `String` としてのフィールド名で、値は常に `Vector{String}` であり、複数のコンポーネントや数値データの場合でも同様です。`MMCIFDict` `d` の基礎となる辞書に直接アクセスするには、`d.dict` を使用します。ファイルパスまたはストリームを指定して `MMCIFDict` を呼び出すことで、そのソースから辞書を読み取ります。キーワード引数 `gzip`（デフォルトは `false`）は、入力がgzippedかどうかを決定します。
