```
build_qa_evals(doc_chunks::Vector{<:AbstractString}, sources::Vector{<:AbstractString};
			   model=PT.MODEL_CHAT, instructions="None.", qa_template::Symbol=:RAGCreateQAFromContext, 
			   verbose::Bool=true, api_kwargs::NamedTuple = NamedTuple(), kwargs...) -> Vector{QAEvalItem}
```

ドキュメントチャンクとソースから質問と回答の評価（`QAEvalItem`）のコレクションを作成します。この関数は、指定されたAIモデルとテンプレートを使用して、提供されたドキュメントチャンクに基づいてQ&Aペアを生成します。

# 引数

  * `doc_chunks::Vector{<:AbstractString}`: 各テキストセグメントを表すドキュメントチャンクのベクター。
  * `sources::Vector{<:AbstractString}`: `doc_chunks`内の各チャンクに対応するソース識別子のベクター（例：ファイル名やパス）。
  * `model`: Q&Aペアを生成するために使用されるAIモデル。デフォルトは`PT.MODEL_CHAT`。
  * `instructions::String`: QAセットを生成するモデルに提供する追加の指示やコンテキスト。デフォルトは"None."。
  * `qa_template::Symbol`: 使用されるAITemplateを決定するテンプレートシンボル。`context`のプレースホルダーを持っている必要があります。デフォルトは`:CreateQAFromContext`。
  * `api_kwargs::NamedTuple`: APIエンドポイントに転送されるパラメータ。
  * `verbose::Bool`: `true`の場合、コストなどの追加情報がログに記録されます。デフォルトは`true`。

# 戻り値

`Vector{QAEvalItem}`: 各ソース、コンテキスト、質問、および回答を含む`QAEvalItem`構造体のベクター。無効または空のアイテムはフィルタリングされます。

# 注意事項

  * この関数は内部的に`aiextract`を使用して、提供された`qa_template`に基づいてQ&Aペアを生成します。したがって、必要なkwargsを使用できます。
  * 各`QAEvalItem`には、コンテキスト（ドキュメントチャンク）、生成された質問と回答、およびソースが含まれます。
  * `verbose`が有効な場合、AIコールのコストを追跡して報告します。
  * 質問、回答、またはコンテキストが空のアイテムは無効と見なされ、フィルタリングされます。

# 例

ドキュメントチャンクのセットからQ&A評価を作成する：

```julia
doc_chunks = ["Text from document 1", "Text from document 2"]
sources = ["source1", "source2"]
qa_evals = build_qa_evals(doc_chunks, sources)
```
