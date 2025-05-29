```
MultiIndex
```

複合インデックスで、複数のChunkIndexオブジェクトとその埋め込みを格納します。

# フィールド

  * `id::Symbol`: 各インデックスの一意の識別子（`CandidateChunks`で正しいインデックスを使用していることを確認するため）
  * `indexes::Vector{<:AbstractChunkIndex}`: 組み合わせるインデックス

アクセサ`indexes`を使用して、個々のインデックスにアクセスします。

# 例

`AbstractChunkIndex`オブジェクトのベクターから`MultiIndex`を作成できます。

```julia
index = build_index(SimpleIndexer(), texts; chunker_kwargs = (; sources))
index_keywords = ChunkKeywordsIndex(index) # 上記と同じチャンクですが、埋め込みの代わりにBM25を追加します

multi_index = MultiIndex([index, index_keywords])
```

異なるタイプのインデックスで`airag`を使用するには、各インデックスの最も近いアイテムを見つける方法を指定する必要があります。

```julia
# 埋め込みのコサイン類似度とキーワードのBM25、MultiIndex内のインデックスと同じ順序
finder = RT.MultiFinder([RT.CosineSimilarity(), RT.BM25Similarity()])

# キーワードが処理（つまり、トークン化）されることを確認するために`processor`を追加することに注意してください
cfg = RAGConfig(; retriever = SimpleRetriever(; processor = RT.KeywordsProcessor(), finder))

# 質問をする
msg = airag(cfg, multi_index; question = "What are the best practices for parallel computing in Julia?")
pprint(msg) # 答えを整形する
```
