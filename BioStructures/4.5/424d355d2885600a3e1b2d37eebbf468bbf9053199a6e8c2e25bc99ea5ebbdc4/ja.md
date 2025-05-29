```
MMTFDict(filepath; gzip=false)
MMTFDict(io; gzip=false)
MMTFDict()
```

マクロ分子伝送フォーマット (MMTF) 辞書。

辞書を使用するには、MMTF.jl パッケージをインポートする必要があります。標準の `Dict` と同様の関数を使用してアクセスできます。キーは `String` としてのフィールド名で、値はさまざまな型です。`MMTFDict` `d` の基礎となる辞書に直接アクセスするには、`d.dict` を使用します。ファイルパスまたはストリームを指定して `MMTFDict` を呼び出すことで、そのソースから辞書を読み取ります。キーワード引数 `gzip` (デフォルトは `false`) は、ファイルが gzipped かどうかを決定します。
