```
KeywordsIndexer <: AbstractIndexBuilder
```

キーワードベースのインデックス (BM25) は `build_index` によって返されます。

デフォルトのチャンク処理、プロセッサ、およびタグ付けには `TextChunker`、`KeywordsProcessor`、および `NoTagger` が使用されます。
