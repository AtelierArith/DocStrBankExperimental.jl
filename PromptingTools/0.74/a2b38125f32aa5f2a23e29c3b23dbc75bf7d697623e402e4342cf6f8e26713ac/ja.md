```
aiembed(prompt_schema::AbstractOpenAISchema,
        doc_or_docs::Union{AbstractString, AbstractVector{<:AbstractString}},
        postprocess::F = identity;
        verbose::Bool = true,
        api_key::String = OPENAI_API_KEY,
        model::String = MODEL_EMBEDDING, 
        http_kwargs::NamedTuple = (retry_non_idempotent = true,
                                   retries = 5,
                                   readtimeout = 120),
        api_kwargs::NamedTuple = NamedTuple(),
        kwargs...) where {F <: Function}
```

`aiembed` 関数は、指定されたモデルを使用して与えられた入力の埋め込みを生成し、埋め込み、ステータス、トークン数、経過時間を含むメッセージオブジェクトを返します。

## 引数

  * `prompt_schema::AbstractOpenAISchema`: プロンプトのスキーマ。
  * `doc_or_docs::Union{AbstractString, AbstractVector{<:AbstractString}}`: 埋め込みを生成するためのドキュメントまたはドキュメントのリスト。
  * `postprocess::F`: 各埋め込みに適用する後処理関数。デフォルトは恒等関数です。
  * `verbose::Bool`: 詳細情報を印刷するかどうかを示すフラグ。デフォルトは `true` です。
  * `api_key::String`: OpenAI API に使用する API キー。デフォルトは `OPENAI_API_KEY` です。
  * `model::String`: 埋め込みを生成するために使用するモデル。デフォルトは `MODEL_EMBEDDING` です。
  * `http_kwargs::NamedTuple`: HTTP リクエストのための追加のキーワード引数。デフォルトは `(retry_non_idempotent = true, retries = 5, readtimeout = 120)` です。
  * `api_kwargs::NamedTuple`: OpenAI API のための追加のキーワード引数。デフォルトは空の `NamedTuple` です。
  * `kwargs...`: 追加のキーワード引数。

## 戻り値

  * `msg`: 埋め込み、ステータス、トークン数、経過時間を含む `DataMessage` オブジェクト。埋め込みにアクセスするには `msg.content` を使用します。

# 例

```julia
msg = aiembed("Hello World")
msg.content # 1536-element JSON3.Array{Float64...
```

複数の文字列を一度に埋め込むことができ、それらは行列に `hcat` されます（つまり、各列は1つの文字列に対応します）。

```julia
msg = aiembed(["Hello World", "How are you?"])
msg.content # 1536×2 Matrix{Float64}:
```

埋め込み間のコサイン距離を計算する予定がある場合は、最初に正規化することができます：

```julia
using LinearAlgebra
msg = aiembed(["embed me", "and me too"], LinearAlgebra.normalize)

# 2つの正規化された埋め込み間のコサイン距離を単純な内積として計算
msg.content' * msg.content[:, 1] # [1.0, 0.787]
```
