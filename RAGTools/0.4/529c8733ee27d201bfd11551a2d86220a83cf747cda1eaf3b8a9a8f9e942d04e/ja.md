```
generate!(
	generator::AbstractGenerator, index::AbstractDocumentIndex, result::AbstractRAGResult;
	verbose::Integer = 1,
	api_kwargs::NamedTuple = NamedTuple(),
	contexter::AbstractContextBuilder = generator.contexter,
	contexter_kwargs::NamedTuple = NamedTuple(),
	answerer::AbstractAnswerer = generator.answerer,
	answerer_kwargs::NamedTuple = NamedTuple(),
	refiner::AbstractRefiner = generator.refiner,
	refiner_kwargs::NamedTuple = NamedTuple(),
	postprocessor::AbstractPostprocessor = generator.postprocessor,
	postprocessor_kwargs::NamedTuple = NamedTuple(),
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...)
```

提供された `generator` と `index` および `result` を使用して応答を生成します。これは RAG パイプラインの第二ステップです（`retrieve` の後）。

`result` を変更して、`result.final_answer` と `result.conversations[:final_answer]` に保存された全会話を返します。

# 注意事項

  * デフォルトのフローは `build_context!` -> `answer!` -> `refine!` -> `postprocess!` です。
  * `contexter` はコンテキストを構築するために使用するメソッドで、例えば `ContextEnumerator` を使用してコンテキストチャンクを単純に列挙します。
  * `answerer` は LLM を使用した標準的な回答生成ステップです。
  * `refiner` ステップは LLM が自分自身を批評し、自分の回答を洗練させることを可能にします。
  * `postprocessor` ステップは回答の追加処理を可能にします。例えば、ログ記録、会話の保存などです。
  * すべてのサブルーチンは `result` オブジェクトを変更して操作し、その部分を追加します。
  * 各ステップの利用可能なサブタイプは `subtypes(AbstractRefiner)` などを使用して発見できます。

# 引数

  * `generator::AbstractGenerator`: 回答生成に使用する `generator`。`SimpleGenerator` または `AdvancedGenerator` である可能性があります。
  * `index::AbstractDocumentIndex`: チャンクとソースを含むインデックス。
  * `result::AbstractRAGResult`: 回答を生成するためのコンテキストと質問を含む結果。
  * `verbose::Integer`: 0より大きい場合、詳細なログ記録を有効にします。
  * `api_kwargs::NamedTuple`: すべての API 呼び出し（`aiembed`、`aigenerate`、および `aiextract`）に転送される API パラメータ。
  * `contexter::AbstractContextBuilder`: コンテキストを構築するために使用するメソッド。デフォルトは `generator.contexter` で、例えば `ContextEnumerator` です。
  * `contexter_kwargs::NamedTuple`: `contexter` 呼び出しに転送される API パラメータ。
  * `answerer::AbstractAnswerer`: 回答生成に使用するメソッド。デフォルトは `generator.answerer` で、例えば `SimpleAnswerer` です。
  * `answerer_kwargs::NamedTuple`: `answerer` 呼び出しに転送される API パラメータ。例:

```
- `model`: 回答生成に使用するモデル。デフォルトは `PT.MODEL_CHAT`。
- `template`: `aigenerate` 関数に使用するテンプレート。デフォルトは `:RAGAnswerFromContext`。
```

  * `refiner::AbstractRefiner`: 回答を洗練するために使用するメソッド。デフォルトは `generator.refiner` で、例えば `NoRefiner` です。
  * `refiner_kwargs::NamedTuple`: `refiner` 呼び出しに転送される API パラメータ。

```
- `model`: 回答生成に使用するモデル。デフォルトは `PT.MODEL_CHAT`。
- `template`: `aigenerate` 関数に使用するテンプレート。デフォルトは `:RAGAnswerRefiner`。
```

  * `postprocessor::AbstractPostprocessor`: 回答の後処理に使用するメソッド。デフォルトは `generator.postprocessor` で、例えば `NoPostprocessor` です。
  * `postprocessor_kwargs::NamedTuple`: `postprocessor` 呼び出しに転送される API パラメータ。
  * `cost_tracker`: 操作の総コストを追跡するための原子カウンター。

参照: `retrieve`、`build_context!`、`ContextEnumerator`、`answer!`、`SimpleAnswerer`、`refine!`、`NoRefiner`、`SimpleRefiner`、`postprocess!`、`NoPostprocessor`

# 例

```julia
Assume we already have `index`

question = "What are the best practices for parallel computing in Julia?"

# Retrieve the relevant chunks - returns RAGResult
result = retrieve(index, question)

# Generate the answer using the default generator, mutates the same result
result = generate!(index, result)

```
