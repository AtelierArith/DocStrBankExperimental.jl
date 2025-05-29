```
build_index(
	indexer::AbstractIndexBuilder, files_or_docs::Vector{<:AbstractString};
	verbose::Integer = 1,
	extras::Union{Nothing, AbstractVector} = nothing,
	index_id = gensym("ChunkEmbeddingsIndex"),
	chunker::AbstractChunker = indexer.chunker,
	chunker_kwargs::NamedTuple = NamedTuple(),
	embedder::AbstractEmbedder = indexer.embedder,
	embedder_kwargs::NamedTuple = NamedTuple(),
	tagger::AbstractTagger = indexer.tagger,
	tagger_kwargs::NamedTuple = NamedTuple(),
	api_kwargs::NamedTuple = NamedTuple(),
	cost_tracker = Threads.Atomic{Float64}(0.0))
```

提供されたファイルパスからRAG（Retriever-Augmented Generation）アプリケーション用のINDEXを構築します。INDEXは、ドキュメントのチャンクとその埋め込み（および潜在的に他の情報）を保存するオブジェクトです。

この関数は、各ファイルまたはドキュメント（`chunker`に依存）を処理し、その内容をチャンクに分割し、これらのチャンクを埋め込み、オプションでメタデータを抽出し、その後この情報を取得可能なインデックスに統合します。

`indexer`およびそのサブコンポーネント（`chunker`、`embedder`、`tagger`）を介して独自のメソッドを定義します。

# 引数

  * `indexer::AbstractIndexBuilder`: 使用するインデックス作成ロジック。デフォルトは`SimpleIndexer()`です。
  * `files_or_docs`: インデックス化される有効なファイルパスまたは文字列ドキュメントのベクター（チャンク化および埋め込み）。使用するモードは`chunker`を介して指定します。
  * `verbose`: ログの冗長性を指定する整数。デフォルトは`1`（高レベルのログ）。`0`は無効です。
  * `extras`: 各チャンクと一緒に保存される追加情報のオプションのベクター。デフォルトは`nothing`です。
  * `index_id`: インデックスの一意の識別子。デフォルトは生成されたシンボルです。
  * `chunker`: ドキュメントを分割するために使用するチャンクロジック。デフォルトは`TextChunker()`です。
  * `chunker_kwargs`: `get_chunks`関数に提供されるパラメータ。`separators`や`max_length`を変更するのに便利です。

      * `sources`: 各チャンクのソースを示す文字列のベクター。デフォルトは`files_or_docs`と等しいです。
  * `embedder`: チャンクを埋め込むために使用する埋め込みロジック。デフォルトは`BatchEmbedder()`です。
  * `embedder_kwargs`: `get_embeddings`関数に提供されるパラメータ。`target_batch_size_length`を変更したり、非同期マップタスク`ntasks`を減らすのに便利です。

      * `model`: 埋め込みに使用するモデル。デフォルトは`PT.MODEL_EMBEDDING`です。
  * `tagger`: チャンクからタグを抽出するために使用するタグ付けロジック。デフォルトは`NoTagger()`、つまりタグ抽出をスキップします。`PassthroughTagger`や`OpenTagger`もあります。
  * `tagger_kwargs`: `get_tags`関数に提供されるパラメータ。

      * `model`: タグ抽出に使用するモデル。デフォルトは`PT.MODEL_CHAT`です。
      * `template`: タグ抽出に使用されるテンプレート。デフォルトは`:RAGExtractMetadataShort`です。
      * `tags`: 各チャンクのタグを直接提供する文字列のベクターのベクター。`tagger::PassthroughTagger`に適用可能です。
  * `api_kwargs`: APIエンドポイントに提供されるパラメータ。提供されている場合、すべてのAPI呼び出しで共有されます。
  * `cost_tracker`: API呼び出しの総コストを追跡するための`Threads.Atomic{Float64}`オブジェクト。親呼び出しに総コストを渡すのに便利です。

# 戻り値

  * `ChunkEmbeddingsIndex`: チャンク、埋め込み、タグ、語彙、およびソースのコンパイルされたインデックスを含むオブジェクト。

参照: `ChunkEmbeddingsIndex`、`get_chunks`、`get_embeddings`、`get_tags`、`CandidateChunks`、`find_closest`、`find_tags`、`rerank`、`retrieve`、`generate!`、`airag`

# 例

```julia
# デフォルトは文字列のベクターを読み込み、それらをチャンク化することです（`TextChunker()`）
index = build_index(SimpleIndexer(), texts; chunker_kwargs = (; max_length=10))

# タグ抽出、文のみを分割し、冗長な出力を持つ別の例
# `test_files`がファイルパスのベクターであると仮定します
indexer = SimpleIndexer(chunker=FileChunker(), tagger=OpenTagger())
index = build_index(indexer, test_files; 
		chunker_kwargs(; separators=[". "]), verbose=true)
```

# 注意

  * 埋め込み入力サイズを超えるエラーが発生した場合は、最初にチャンクの`max_length`を確認してください。それでも問題が解決しない場合は、`embedding_kwargs`を変更してみてください。特に、`target_batch_size_length`パラメータ（例：10_000）とタスク数`ntasks=1`を減らすことをお勧めします。一部のプロバイダーは大きなバッチサイズを処理できません（例：Databricks）。

```
