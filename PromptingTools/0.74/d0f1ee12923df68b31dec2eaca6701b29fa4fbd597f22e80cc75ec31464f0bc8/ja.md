```
aiembed(prompt_schema::AbstractOllamaManagedSchema,
        doc_or_docs::Union{AbstractString, AbstractVector{<:AbstractString}},
        postprocess::F = identity;
        verbose::Bool = true,
        api_key::String = "",
        model::String = MODEL_EMBEDDING,
        http_kwargs::NamedTuple = (retry_non_idempotent = true,
                                   retries = 5,
                                   readtimeout = 120),
        api_kwargs::NamedTuple = NamedTuple(),
        kwargs...) where {F <: Function}
```

`aiembed` 関数は、指定されたモデルを使用して与えられた入力の埋め込みを生成し、埋め込み、ステータス、トークン数、経過時間を含むメッセージオブジェクトを返します。

## 引数

  * `prompt_schema::AbstractOllamaManagedSchema`: プロンプトのスキーマ。
  * `doc_or_docs::Union{AbstractString, AbstractVector{<:AbstractString}}`: 埋め込みを生成するためのドキュメントまたはドキュメントのリスト。ドキュメントのリストは順次処理されるため、ユーザーは `Threads.@spawn` を使用して非同期バージョンを実装することを検討すべきです。
  * `postprocess::F`: 各埋め込みに適用する後処理関数。デフォルトは恒等関数ですが、`LinearAlgebra.normalize` になる可能性があります。
  * `verbose::Bool`: 詳細情報を印刷するかどうかを示すフラグ。デフォルトは `true`。
  * `api_key::String`: OpenAI API に使用する API キー。デフォルトは `""`。
  * `model::String`: 埋め込みを生成するために使用するモデル。デフォルトは `MODEL_EMBEDDING`。
  * `http_kwargs::NamedTuple`: HTTP リクエストのための追加のキーワード引数。デフォルトは空の `NamedTuple`。
  * `api_kwargs::NamedTuple`: Ollama API のための追加のキーワード引数。デフォルトは空の `NamedTuple`。
  * `kwargs`: プロンプト/テンプレートを埋めるために使用されるプロンプト変数

## 戻り値

  * `msg`: 埋め込み、ステータス、トークン数、経過時間を含む `DataMessage` オブジェクト。

注: 現在、Ollama API はトークン数を返さないため、`(0,0)` に設定されています。

# 例

```julia
const PT = PromptingTools
schema = PT.OllamaManagedSchema()

msg = aiembed(schema, "Hello World"; model="openhermes2.5-mistral")
msg.content # 4096-element JSON3.Array{Float64...
```

複数の文字列を一度に埋め込むことができ、`hcat` で行列にまとめられます（つまり、各列は1つの文字列に対応します）。

```julia
const PT = PromptingTools
schema = PT.OllamaManagedSchema()

msg = aiembed(schema, ["Hello World", "How are you?"]; model="openhermes2.5-mistral")
msg.content # 4096×2 Matrix{Float64}:
```

埋め込み間のコサイン距離を計算する予定がある場合は、最初に正規化することができます。

```julia
const PT = PromptingTools
using LinearAlgebra
schema = PT.OllamaManagedSchema()

msg = aiembed(schema, ["embed me", "and me too"], LinearAlgebra.normalize; model="openhermes2.5-mistral")

# 2つの正規化された埋め込み間のコサイン距離を単純な内積として計算
msg.content' * msg.content[:, 1] # [1.0, 0.34]
```

同様に、`postprocess` 引数を使用して、`postprocess = copy` を使用して JSON3.Object からデータを具現化することができます。

```julia
const PT = PromptingTools
schema = PT.OllamaManagedSchema()

msg = aiembed(schema, "Hello World", copy; model="openhermes2.5-mistral")
msg.content # 4096-element Vector{Float64}
```
