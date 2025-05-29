```
refine!(
	refiner::TavilySearchRefiner, index::AbstractDocumentIndex, result::AbstractRAGResult;
	verbose::Bool = true,
	model::AbstractString = PT.MODEL_CHAT,
	include_answer::Bool = true,
	max_results::Integer = 5,
	include_domains::AbstractVector{<:AbstractString} = String[],
	exclude_domains::AbstractVector{<:AbstractString} = String[],
	template::Symbol = :RAGWebSearchRefiner,
	cost_tracker = Threads.Atomic{Float64}(0.0),
	kwargs...)
```

Tavily APIを使用してウェブ検索を実行することで、回答を洗練します。このメソッドは、ウェブから取得した情報を組み込むことで、回答の正確性と関連性を向上させることを目的としています。

注意: ウェブ結果とウェブ回答（要求された場合）は、コンテキストとソースに追加されます！

# 戻り値

  * `result`が変異し、`result.final_answer`と完全な会話が`result.conversations[:final_answer]`に保存されます。
  * さらに、ウェブ結果とウェブ回答（要求された場合）が`result.context`と`result.sources`に追加され、正しいハイライトと検証が行われます。

# 引数

  * `refiner::TavilySearchRefiner`: 回答を洗練するために使用するメソッド。ウェブ検索テンプレートを使用して`aigenerate`を実行します。
  * `index::AbstractDocumentIndex`: チャンクとソースを含むインデックス。
  * `result::AbstractRAGResult`: 回答を生成するためのコンテキストと質問を含む結果。
  * `model::AbstractString`: 回答を生成するために使用するモデル。デフォルトは`PT.MODEL_CHAT`です。
  * `include_answer::Bool`: `true`の場合、ウェブ検索にTavilyからの回答を含めます。
  * `max_results::Integer`: 戻り値の最大結果数。
  * `include_domains::AbstractVector{<:AbstractString}`: 検索結果に含めるドメインのリスト。デフォルトは空のリストです。
  * `exclude_domains::AbstractVector{<:AbstractString}`: 検索結果から除外するドメインのリスト。デフォルトは空のリストです。
  * `verbose::Bool`: `true`の場合、詳細なログを有効にします。
  * `template::Symbol`: `aigenerate`関数に使用するテンプレート。デフォルトは`:RAGWebSearchRefiner`です。
  * `cost_tracker`: 操作のコストを追跡するためのアトミックカウンター。

# 例

```julia
refiner!(TavilySearchRefiner(), index, result)
# result.final_answerを確認するか、pprint(result)を実行します
```

このリファイナーを完全なRAGパイプラインで有効にするには、構成内のコンポーネントを単に入れ替えます：

```julia
cfg = RT.RAGConfig()
cfg.generator.refiner = RT.TavilySearchRefiner()

result = airag(cfg, index; question, return_all = true)
pprint(result)
```
