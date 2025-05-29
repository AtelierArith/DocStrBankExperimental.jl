```
AdvancedRetriever <: AbstractRetriever
```

高度な検索方法を使用して結果の質を向上させるための`retrieve`のディスパッチ。SimpleRetrieverと比較して、クエリの言い換えと結果の再ランキングを追加します。

# フィールド

  * `rephraser::AbstractRephraser`: 言い換え方法、`rephrase`をディスパッチ - `HyDERephraser`を使用
  * `embedder::AbstractEmbedder`: 埋め込み方法、`get_embeddings`をディスパッチ（詳細は準備段階を参照） - `BatchEmbedder`を使用
  * `processor::AbstractProcessor`: 処理方法、`get_keywords`をディスパッチ（詳細は準備段階を参照） - `NoProcessor`を使用
  * `finder::AbstractSimilarityFinder`: 類似検索方法、`find_closest`をディスパッチ - `CosineSimilarity`を使用
  * `tagger::AbstractTagger`: タグ生成方法、`get_tags`をディスパッチ（詳細は準備段階を参照） - `NoTagger`を使用
  * `filter::AbstractTagFilter`: タグ一致方法、`find_tags`をディスパッチ - `NoTagFilter`を使用
  * `reranker::AbstractReranker`: 再ランキング方法、`rerank`をディスパッチ - `CohereReranker`を使用
