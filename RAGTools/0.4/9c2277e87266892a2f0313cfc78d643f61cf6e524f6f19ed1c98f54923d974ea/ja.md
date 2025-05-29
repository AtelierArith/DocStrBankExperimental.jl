```
SimpleBM25Retriever <: AbstractRetriever
```

キーワードベースの`retrieve`の実装です。`BM25Similarity`を介して単純な類似性検索を行い、結果を返します。

一貫した`processor`と`tagger`を準備段階（`build_index`）で使用することを確認してください！

# フィールド

  * `rephraser::AbstractRephraser`: 言い換えメソッド、`rephrase`をディスパッチ - `NoRephraser`を使用
  * `embedder::AbstractEmbedder`: 埋め込みメソッド、`get_embeddings`をディスパッチ（詳細は準備段階を参照） - `NoEmbedder`を使用
  * `processor::AbstractProcessor`: プロセッサメソッド、`get_keywords`をディスパッチ（詳細は準備段階を参照） - `KeywordsProcessor`を使用
  * `finder::AbstractSimilarityFinder`: 類似性検索メソッド、`find_closest`をディスパッチ - `CosineSimilarity`を使用
  * `tagger::AbstractTagger`: タグ生成メソッド、`get_tags`をディスパッチ（詳細は準備段階を参照） - `NoTagger`を使用
  * `filter::AbstractTagFilter`: タグマッチングメソッド、`find_tags`をディスパッチ - `NoTagFilter`を使用
  * `reranker::AbstractReranker`: 再ランキングメソッド、`rerank`をディスパッチ - `NoReranker`を使用
