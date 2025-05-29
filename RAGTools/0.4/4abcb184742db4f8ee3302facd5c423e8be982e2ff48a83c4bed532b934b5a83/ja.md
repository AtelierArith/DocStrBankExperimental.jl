```
SimpleIndexer <: AbstractIndexBuilder
```

`build_index` のデフォルト実装です。

デフォルトのチャンク処理、埋め込み、タグ付けには `TextChunker`、`BatchEmbedder`、および `NoTagger` を使用します。
