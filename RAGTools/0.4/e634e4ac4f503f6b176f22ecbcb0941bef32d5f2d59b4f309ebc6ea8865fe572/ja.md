```
retrieve(
	retriever::AbstractRetriever,
	index::AbstractChunkIndex,
	question::AbstractString;
	verbose::Integer = 1,
	top_k::Integer = 100,
	top_n::Integer = 5,
	api_kwargs::NamedTuple = NamedTuple(),
	rephraser::AbstractRephraser = retriever.rephraser,
	rephraser_kwargs::NamedTuple = NamedTuple(),
	embedder::AbstractEmbedder = retriever.embedder,
	embedder_kwargs::NamedTuple = NamedTuple(),
	processor::AbstractProcessor = retriever.processor,
	processor_kwargs::NamedTuple = NamedTuple(),
	finder::AbstractSimilarityFinder = retriever.finder,
	finder_kwargs::NamedTuple = NamedTuple(),
	tagger::AbstractTagger = retriever.tagger,
	tagger_kwargs::NamedTuple = NamedTuple(),
	filter::AbstractTagFilter = retriever.filter,
	filter_kwargs::NamedTuple = NamedTuple(),
	reranker::AbstractReranker = retriever.reranker,
	reranker_kwargs::NamedTuple = NamedTuple(),
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...,
)
```

与えられた質問に対して、インデックスから最も関連性の高いチャンクを取得し、`RAGResult`オブジェクトに返します。

これはRAGパイプラインの取得ステージの主要なエントリポイントです。通常、`generate!`ステップが続きます。

注意:

  * デフォルトのフローは`build_context!` -> `answer!` -> `refine!` -> `postprocess!`です。

引数は取得プロセスの各ステップ（言い換え、埋め込み、類似文書の検索、タグ付け、タグによるフィルタリング、再ランキング）に対応しています。各ステップをカスタマイズするには、対応する関数をディスパッチする新しいカスタムタイプを提供します。例えば、自分のタイプ`struct MyReranker<:AbstractReranker end`を作成し、それに対するカスタムメソッド`rerank(::MyReranker,...) = ...`を定義します。

注意: 各ステップの利用可能な取得サブタイプを`subtypes(AbstractRephraser)`で発見し、他の抽象型についても同様です。

ローカルホストされたモデルを使用している場合、`api_kwargs`にモデルのURLを設定した`url`フィールドを渡し、`rephraser`、`embedder`、`tagger`にカスタムモデルを使用するための対応する`model` kwargsを提供することを確認してください（これらはAI呼び出しを行います）。

# 引数

  * `retriever`: 使用する取得方法。デフォルトは`SimpleRetriever`ですが、より高度な取得のために`AdvancedRetriever`を使用することもできます。
  * `index`: 取得するチャンクとソースを保持するインデックス。
  * `question`: 取得に使用する質問。
  * `verbose`: `>0`の場合、詳細なログを出力します。デフォルトは`1`です。`2`に設定すると、各サブ関数のログが出力されます。
  * `top_k`: `find_closest`から返す最も近いチャンクの合計数。デフォルトは`100`です。複数の言い換えられた質問がある場合、各アイテムごとのチャンク数は`top_k ÷ number_of_rephrased_questions`になります。
  * `top_n`: コンテキストのために返す最も関連性の高いチャンクの合計数（`rerank`ステップから）。デフォルトは`5`です。
  * `api_kwargs`: API呼び出しに渡される追加のキーワード引数（すべての`ai*`呼び出しで共有）。
  * `rephraser`: 質問を1つ以上の質問に変換します。デフォルトは`retriever.rephraser`です。
  * `rephraser_kwargs`: 言い換え器に渡される追加のキーワード引数。

```
- `model`: 言い換えに使用するモデル。デフォルトは`PT.MODEL_CHAT`です。
- `template`: 使用する言い換えテンプレート。デフォルトは`:RAGQueryOptimizer`または`:RAGQueryHyDE`（選択した`rephraser`に依存）。
```

  * `embedder`: 使用する埋め込み方法。デフォルトは`retriever.embedder`です。
  * `embedder_kwargs`: 埋め込み器に渡される追加のキーワード引数。
  * `processor`: キーワードベースのインデックスを使用する際に使用するプロセッサ方法。デフォルトは`retriever.processor`です。
  * `processor_kwargs`: プロセッサに渡される追加のキーワード引数。
  * `finder`: 使用する類似検索方法。デフォルトは`retriever.finder`、通常は`CosineSimilarity`です。
  * `finder_kwargs`: 類似性ファインダーに渡される追加のキーワード引数。
  * `tagger`: 使用するタグ生成方法。デフォルトは`retriever.tagger`です。
  * `tagger_kwargs`: タグ付け器に渡される追加のキーワード引数。注目すべき引数:

```
- `tags`: フィルタリングに使用するタグを直接提供します（String、Regex、またはVector{String}のいずれか）。`tagger = PassthroughTagger`に便利です。
```

  * `filter`: 使用するタグ一致方法。デフォルトは`retriever.filter`です。
  * `filter_kwargs`: タグフィルタに渡される追加のキーワード引数。
  * `reranker`: 使用する再ランキング方法。デフォルトは`retriever.reranker`です。
  * `reranker_kwargs`: 再ランキング器に渡される追加のキーワード引数。

```
- `model`: 再ランキングに使用するモデル。デフォルトは`rerank-english-v2.0`で、`reranker = CohereReranker()`を使用する場合。
```

  * `cost_tracker`: 取得のコストを追跡するためのアトミックカウンター。デフォルトは`Threads.Atomic{Float64}(0.0)`です。

参照: `SimpleRetriever`, `AdvancedRetriever`, `build_index`, `rephrase`, `get_embeddings`, `get_keywords`, `find_closest`, `get_tags`, `find_tags`, `rerank`, `RAGResult`。

# 例

与えられた質問に対してインデックスから最も関連性の高い5つのチャンクを見つけます。

```julia
# 既存のインデックス`index`があると仮定
retriever = SimpleRetriever()

result = retrieve(retriever,
	index,
	"What is the capital of France?",
	top_n = 5)

# またはデフォルトのリトリーバーを使用（上記と同じ）
result = retrieve(retriever,
	index,
	"What is the capital of France?",
	top_n = 5)
```

質問の言い換えと再ランキングを使用して、より高度な取得を適用します（`COHERE_API_KEY`が必要）。埋め込みから上位100チャンク（`top_k`）と再ランキングから上位5チャンク（`top_n`）を取得します。

```julia
retriever = AdvancedRetriever()

result = retrieve(retriever, index, question; top_k=100, top_n=5)
```

`retriever`を使用して取得戦略をカスタマイズするか、`retrieve`のkwargsで戦略タイプを直接変更できます！

`localhost:8080`でホストされたローカルホストモデルを使用する例：

```julia
retriever = SimpleRetriever()
result = retrieve(retriever, index, question;
	rephraser_kwargs = (; model = "custom"),
	embedder_kwargs = (; model = "custom"),
	tagger_kwargs = (; model = "custom"), api_kwargs = (;
		url = "http://localhost:8080"))
```
