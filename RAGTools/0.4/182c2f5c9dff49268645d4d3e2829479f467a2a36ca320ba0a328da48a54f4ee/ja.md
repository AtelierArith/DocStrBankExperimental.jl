```
SimpleRetriever <: AbstractRetriever
```

`retrieve` 関数のデフォルト実装です。`CosineSimilarity` を介して単純な類似性検索を行い、結果を返します。

準備段階（`build_index`）で一貫した `embedder` と `tagger` を使用することを確認してください！

# フィールド

  * `rephraser::AbstractRephraser`: 言い換えメソッドで、`rephrase` をディスパッチします - `NoRephraser` を使用
  * `embedder::AbstractEmbedder`: 埋め込みメソッドで、`get_embeddings` をディスパッチします（詳細は準備段階を参照） - `BatchEmbedder` を使用
  * `processor::AbstractProcessor`: プロセッサメソッドで、`get_keywords` をディスパッチします（詳細は準備段階を参照） - `NoProcessor` を使用
  * `finder::AbstractSimilarityFinder`: 類似性検索メソッドで、`find_closest` をディスパッチします - `CosineSimilarity` を使用
  * `tagger::AbstractTagger`: タグ生成メソッドで、`get_tags` をディスパッチします（詳細は準備段階を参照） - `NoTagger` を使用
  * `filter::AbstractTagFilter`: タグマッチングメソッドで、`find_tags` をディスパッチします - `NoTagFilter` を使用
  * `reranker::AbstractReranker`: 再ランキングメソッドで、`rerank` をディスパッチします - `NoReranker` を使用
