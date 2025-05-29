```
airag(cfg::AbstractRAGConfig, index::AbstractDocumentIndex;
	question::AbstractString,
	verbose::Integer = 1, return_all::Bool = false,
	api_kwargs::NamedTuple = NamedTuple(),
	retriever::AbstractRetriever = cfg.retriever,
	retriever_kwargs::NamedTuple = NamedTuple(),
	generator::AbstractGenerator = cfg.generator,
	generator_kwargs::NamedTuple = NamedTuple(),
	cost_tracker = Threads.Atomic{Float64}(0.0))
```

Retrieval-Augmented Generation (RAG) の高レベルラッパーで、必要に応じてカスタマイズできる `retrieve` と `generate!` ステップを組み合わせます。

最もシンプルなバージョンは、まず `index` から `question` に関連するチャンクを見つけ、次にこれらのチャンクを AI モデルに送信して `question` に対する応答を生成するのを助けます。

コンポーネントをカスタマイズするには、RAG パイプラインの対応するステップの型（`retriever`、`generator`）を置き換えるか、ステップ内のサブルーチンに入ります。例えば、`subtypes(AbstractRetriever)` を使用して利用可能なオプションを見つけます。

# 引数

  * `cfg::AbstractRAGConfig`: RAG パイプラインの設定。デフォルトは `RAGConfig()` で、サブタイプを入れ替えてパイプラインをカスタマイズできます。
  * `index::AbstractDocumentIndex`: 関連するテキストを検索するためのチャンクインデックス。
  * `question::AbstractString`: 答えられるべき質問。
  * `return_all::Bool`: `true` の場合、応答とともに RAG に使用された詳細を返します。
  * `verbose::Integer`: `>0` の場合、詳細なログを有効にします。数値が大きいほど、より多くのネストされた関数がログを記録します。
  * `api_kwargs`: すべての API 呼び出し（`aiembed`、`aigenerate`、および `aiextract`）に転送される API パラメータ。
  * `retriever::AbstractRetriever`: 関連するチャンクを見つけるために使用するリトリーバー。デフォルトは `cfg.retriever`、例えば `SimpleRetriever`（質問の言い換えなし）。
  * `retriever_kwargs::NamedTuple`: `retriever` 呼び出しに転送される API パラメータ。重要なものの例：

```
- `top_k::Int`: 埋め込みの類似性に基づいて取得する上位候補の数。
- `top_n::Int`: 再ランク付け後に返す候補の数。
- `tagger::AbstractTagger`: チャンクにタグ付けするために使用するタグ付けツール。デフォルトは `NoTagger()`。
- `tagger_kwargs::NamedTuple`: `tagger` 呼び出しに転送される API パラメータ。`PassthroughTagger` を使用して明示的なタグを直接提供し、`tagger_kwargs = (; tags = ["tag1", "tag2"])` とすることができます。
```

  * `generator::AbstractGenerator`: 答えを生成するために使用するジェネレーター。デフォルトは `cfg.generator`、例えば `SimpleGenerator`。
  * `generator_kwargs::NamedTuple`: `generator` 呼び出しに転送される API パラメータ。重要なものの例：

```
- `answerer_kwargs::NamedTuple`: `answerer` 呼び出しに転送される API パラメータ。例：
	- `model`: 答えを生成するために使用するモデル。デフォルトは `PT.MODEL_CHAT`。
	- `template`: `aigenerate` 関数に使用するテンプレート。デフォルトは `:RAGAnswerFromContext`。
- `refiner::AbstractRefiner`: 答えを洗練させるために使用する方法。デフォルトは `generator.refiner`、例えば `NoRefiner`。
- `refiner_kwargs::NamedTuple`: `refiner` 呼び出しに転送される API パラメータ。
	- `model`: 答えを生成するために使用するモデル。デフォルトは `PT.MODEL_CHAT`。
	- `template`: `aigenerate` 関数に使用するテンプレート。デフォルトは `:RAGAnswerRefiner`。
```

  * `cost_tracker`: 操作の総コストを追跡するための原子カウンター（複数のパイプライン実行のコストを追跡したい場合 - パイプライン内で渡されます）。

# 戻り値

  * `return_all` が `false` の場合、生成されたメッセージ（`msg`）を返します。
  * `return_all` が `true` の場合、`RAGResult` におけるフルパイプラインの詳細を返します（ドキュメントを参照）。

`build_index`、`retrieve`、`generate!`、`RAGResult`、`getpropertynested`、`setpropertynested`、`merge_kwargs_nested`、`ChunkKeywordsIndex` も参照してください。

# 例

質問に対する応答を得るために `airag` を使用する：

```julia
index = build_index(...)  # インデックスを作成
question = "Makie.jl でバープロットを作成するには？"
msg = airag(index; question)
```

RAG プロセスの詳細を理解するには、`return_all=true` を使用します。

```julia
msg, details = airag(index; question, return_all = true)
# details は `airag` 関数のすべての内部ステップを持つ RAGDetails オブジェクトです
```

生成されたテキストとコンテキストによってサポートされるテキストを強調表示するために、`details` をきれいに印刷することもできます。また、応答の各部分に使用されたコンテキストの注釈も含まれています（利用可能な場合）。

```julia
PT.pprint(details)
```

質問の言い換えと再ランク付けを伴う高度なリトリーバルの例（`COHERE_API_KEY` が必要）。埋め込みから上位 100 チャンク（`top_k`）を取得し、再ランク付けから上位 5 チャンク（`top_n`）を取得します。さらに、"カスタム" のローカルホストモデルで行います。

```julia
cfg = RAGConfig(; retriever = AdvancedRetriever())

# kwargs は大きくネストされるので、事前に準備します
# LLM を呼び出す各コンポーネントに "custom" モデルを指定します
kwargs = (
	retriever_kwargs = (;
		top_k = 100,
		top_n = 5,
		rephraser_kwargs = (;
			model = "custom"),
		embedder_kwargs = (;
			model = "custom"),
		tagger_kwargs = (;
			model = "custom")),
	generator_kwargs = (;
		answerer_kwargs = (;
			model = "custom"),
		refiner_kwargs = (;
			model = "custom")),
	api_kwargs = (;
		url = "http://localhost:8080"))

result = airag(cfg, index, question; kwargs...)
```

ハイブリッドリトリーバル（埋め込み + BM25）を使用したい場合は、キーワードに基づいて追加のインデックスを簡単に作成し、両方を `MultiIndex` に渡すことができます。

明示的な設定を提供する必要があるため、パイプラインは検索類似性フェーズ（`finder`）で各インデックスをどのように処理するかを知っています。

```julia
index = # 既存のインデックス

# キーワードインデックスでマルチインデックスを作成
index_keywords = ChunkKeywordsIndex(index)
multi_index = MultiIndex([index, index_keywords])

# 持っているインデックスの類似性測定を定義します（同じ順序）
finder = RT.MultiFinder([RT.CosineSimilarity(), RT.BM25Similarity()])
cfg = RAGConfig(; retriever=AdvancedRetriever(; processor=RT.KeywordsProcessor(), finder))

# 新しいハイブリッドリトリーバルでパイプラインを実行します（詳細を見るために `RAGResult` を返します）
result = airag(cfg, multi_index; question, return_all=true)

# 結果をきれいに印刷
PT.pprint(result)
```

ネストされた kwargs の操作を容易にするために、ユーティリティ `getpropertynested`、`setpropertynested`、`merge_kwargs_nested` を参照してください。 ```
