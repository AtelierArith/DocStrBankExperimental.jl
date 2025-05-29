```
ChunkKeywordsIndex
```

BM25類似性検索のためのテキストのチャンクと関連するキーワードを格納する構造体。

# フィールド

  * `id::Symbol`: 各インデックスの一意の識別子（`CandidateChunks`と正しいインデックスを使用していることを確認するため）
  * `chunks::Vector{<:AbstractString}`: 基本となる文書のチャンク / スニペット
  * `chunkdata::Union{Nothing, AbstractMatrix{<:Real}}`: 類似性検索用、`DocumentTermMatrix`であると仮定
  * `tags::Union{Nothing, AbstractMatrix{<:Bool}}`: 正確な検索、フィルタリングなどのため。これは、与えられた`tag`を持つチャンクを示すスパース行列であることが多い（位置のルックアップについては`tag_vocab`を参照）
  * `tags_vocab::Union{Nothing, Vector{<:AbstractString}}`: `tags`行列の語彙（`tags`の各列は`tags_vocab`の1つのアイテムであり、行はチャンク）
  * `sources::Vector{<:AbstractString}`: チャンクのソース
  * `extras::Union{Nothing, AbstractVector}`: 追加データ、例えばメタデータ、ソースコードなど。

# 例

標準の埋め込みベースのインデックスからキーワードベースのインデックスを簡単に作成できます。

```julia

# 標準の埋め込みベースのインデックスがあると仮定しましょう
index = build_index(SimpleIndexer(), texts; chunker_kwargs = (; max_length=10))

# キーワードベースの検索（BM25）のための追加インデックスを作成するのは簡単です
index_keywords = ChunkKeywordsIndex(index)

# すぐに両方のインデックスを保持するハイブリッドインデックス（MultiIndex）を作成できます
multi_index = MultiIndex([index, index_keywords])

```

build_indexを介してインデックスを構築することもできます。

```julia
# いくつかの文とソースが与えられた場合
index_keywords = build_index(KeywordsIndexer(), sentences; chunker_kwargs=(; sources))

# 最も近いチャンクを取得するには
retriever = SimpleBM25Retriever()
result = retrieve(retriever, index_keywords, "Juliaにおける並列計算のベストプラクティスは何ですか？")
result.context
```

airagを使用したい場合は、キーワードが処理される（つまり、トークン化される）ことを確認し、BM25が候補の検索に使用されるように設定を指定することを忘れないでください。

```julia
cfg = RAGConfig(; retriever = SimpleBM25Retriever());
airag(cfg, index_keywords;
	question = "Juliaにおける並列計算のベストプラクティスは何ですか？")
```
