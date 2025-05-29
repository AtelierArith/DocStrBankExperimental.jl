```
aiscan([prompt_schema::AbstractOllamaSchema,] prompt::ALLOWED_PROMPT_TYPE; 
image_url::Union{Nothing, AbstractString, Vector{<:AbstractString}} = nothing,
image_path::Union{Nothing, AbstractString, Vector{<:AbstractString}} = nothing,
attach_to_latest::Bool = true,
verbose::Bool = true, api_key::String = OPENAI_API_KEY,
    model::String = MODEL_CHAT,
    return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    http_kwargs::NamedTuple = (;
        retry_non_idempotent = true,
        retries = 5,
        readtimeout = 120), 
    api_kwargs::NamedTuple = = (; max_tokens = 2500),
    kwargs...)
```

提供された画像（`image_url`または`image_path`）を、`prompt`で指定された目的でスキャンします。

OCR（画像内のテキストを転写）、画像キャプショニング、画像分類など、多くのマルチモーダルタスクに使用できます。

これは、追加のキーワード引数`image_url`、`image_path`、`image_detail`を提供する必要がある`aigenerate`呼び出しの軽いラッパーです。少なくとも1つの画像ソース（URLまたはパス）を提供する必要があります。

# 引数

  * `prompt_schema`: 適用すべきプロンプトテンプレートを指定するためのオプションオブジェクト（デフォルトは`PROMPT_SCHEMA = OpenAISchema`）
  * `prompt`: AIとの会話のためのプロンプトを表す文字列、`UserMessage`、`AbstractMessage`のベクター、または`AITemplate`であることができます。
  * `image_url`: スキャンする画像のURLを表す文字列または文字列のベクター。
  * `image_path`: スキャンする画像のパスを表す文字列または文字列のベクター。
  * `image_detail`: 画像に含める詳細レベルを表す文字列。`"auto"`、`"high"`、または`"low"`のいずれかです。詳細については[OpenAI Vision Guide](https://platform.openai.com/docs/guides/vision)を参照してください。
  * `attach_to_latest`: 複数の`UserMessage`が提供された場合の処理方法を示すブール値。`true`の場合、画像は最新の`UserMessage`に添付されます。
  * `verbose`: 追加情報を印刷するかどうかを示すブール値。
  * `api_key`: OpenAI APIにアクセスするためのAPIキーを表す文字列。
  * `model`: 応答生成に使用するモデルを表す文字列。`MODEL_ALIASES`で定義されたモデルIDに対応するエイリアスであることができます。
  * `return_all::Bool=false`: `true`の場合、会話履歴全体を返し、そうでない場合は最後のメッセージ（`AIMessage`）のみを返します。
  * `dry_run::Bool=false`: `true`の場合、モデルにメッセージを送信するのをスキップします（デバッグ用、通常は`return_all=true`と一緒に使用されます）。
  * `conversation`: 会話履歴を表す`AbstractMessage`オブジェクトのオプションベクター。提供されない場合は、空のベクターとして初期化されます。
  * `http_kwargs`: HTTPキーワード引数の名前付きタプル。
  * `api_kwargs`: APIキーワード引数の名前付きタプル。
  * `kwargs`: プロンプト/テンプレートを埋めるために使用されるプロンプト変数

# 戻り値

`return_all=false`（デフォルト）の場合：

  * `msg`: 生成されたAIメッセージを表す`AIMessage`オブジェクトで、内容、ステータス、トークン、経過時間が含まれます。

抽出された文字列にアクセスするには`msg.content`を使用します。

`return_all=true`の場合：

  * `conversation`: AIモデルからの応答（`AIMessage`）を含む、完全な会話履歴を表す`AbstractMessage`オブジェクトのベクター。

また、`ai_str`、`aai_str`、`aigenerate`、`aiembed`、`aiclassify`、`aiextract`、`aitemplates`も参照してください。

# 注意事項

  * 以下のすべての例は、モデルID "gpt-4-vision-preview"のエイリアスであるモデル "gpt4v"を使用しています。
  * `api_kwargs`の`max_tokens`は2500にプリセットされており、そうでない場合はOpenAIがデフォルトで数百トークン（約300）に制限します。出力が切り捨てられる場合は、この値を増やしてください。

# 例

提供された画像を説明します：

```julia
msg = aiscan("Describe the image"; image_path="julia.png", model="bakllava")
# [ Info: Tokens: 1141 @ Cost: $0.0117 in 2.2 seconds
# AIMessage("The image shows a logo consisting of the word "julia" written in lowercase")
```

複数の画像をベクターとして一度に提供し、"low"レベルの詳細を要求できます（コストが安い）：

```julia
msg = aiscan("Describe the image"; image_path=["julia.png","python.png"] model="bakllava")
```

この関数を使って、テンプレート`:OCRTask`を使用した素早いOCR（画像内のテキストを転写）を行うことができます。スクリーンショットからSQLコードを転写しましょう（再入力は不要です！）：

```julia
using Downloads
# SQLコードのスクリーンショット -- 直接image_urlを使用できないため、最初にダウンロードする必要があります
image_url = "https://www.sqlservercentral.com/wp-content/uploads/legacy/8755f69180b7ac7ee76a69ae68ec36872a116ad4/24622.png"
image_path = Downloads.download(image_url)
msg = aiscan(:OCRTask; image_path, model="bakllava", task="Transcribe the SQL code in the image.", api_kwargs=(; max_tokens=2500))

# AIMessage("```sql
# update Orders <continue>

# 出力の構文ハイライトをMarkdownを介して追加できます
using Markdown
msg.content |> Markdown.parse
```

ローカルモデルは画像URL（`image_url`）を直接処理できないため、最初に画像をダウンロードし、`image_path`として提供する必要があります：

```julia
using Downloads
image_path = Downloads.download(image_url)
```

`max_tokens = 2500`を設定したことに注意してください。出力が切り捨てられているように見える場合は、サーバーのデフォルトの最大トークンが低すぎるためかもしれません！ ```
