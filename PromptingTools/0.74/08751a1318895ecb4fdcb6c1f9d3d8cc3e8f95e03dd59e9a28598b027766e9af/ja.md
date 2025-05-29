```
aiimage(prompt_schema::AbstractOpenAISchema, prompt::ALLOWED_PROMPT_TYPE;
    image_size::AbstractString = "1024x1024",
    image_quality::AbstractString = "standard",
    image_n::Integer = 1,
    verbose::Bool = true,
    api_key::String = OPENAI_API_KEY,
    model::String = MODEL_IMAGE_GENERATION,
    return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    http_kwargs::NamedTuple = (retry_non_idempotent = true,
        retries = 5,
        readtimeout = 120), api_kwargs::NamedTuple = NamedTuple(),
    kwargs...)
```

提供された `prompt` から画像を生成します。複数の「メッセージ」が `prompt` に提供されている場合、最後のメッセージからのみテキストを抽出します！

画像（またはその参照）は `DataMessage.content` に返され、フォーマットは設定した `api_kwargs.response_format` に依存します。

`dall-e-*` モデルを使用して、さまざまな品質とスタイルの画像を生成するために使用できます。この関数はマルチターンの会話をサポートしていません（つまり、`conversation` 引数を介して以前の会話を提供しないでください）。

# 引数

  * `prompt_schema`: 適用すべきプロンプトテンプレートを指定するためのオプションオブジェクト（デフォルトは `PROMPT_SCHEMA = OpenAISchema`）
  * `prompt`: AI会話のプロンプトを表す文字列、`UserMessage`、`AbstractMessage` のベクトル、または `AITemplate` である可能性があります
  * `image_size`: 画像の解像度を表す文字列、例: "1024x1024"。サポートされている解像度は限られています - [APIドキュメント](https://platform.openai.com/docs/api-reference/images/create)を参照してください。
  * `image_quality`: "standard" または "hd" のいずれかです。デフォルトは "standard"。
  * `image_n`: 生成する画像の数。現在、単一の画像生成のみが許可されています（`image_n = 1`）。
  * `verbose`: 追加情報を印刷するかどうかを示すブール値。
  * `api_key`: OpenAI APIにアクセスするためのAPIキーを表す文字列。
  * `model`: 応答生成に使用するモデルを表す文字列。`MODEL_IMAGE_GENERATION` に定義されたモデルIDに対応するエイリアスである可能性があります。
  * `return_all::Bool=false`: `true` の場合、会話履歴全体を返し、そうでない場合は最後のメッセージ（`AIMessage`）のみを返します。
  * `dry_run::Bool=false`: `true` の場合、モデルにメッセージを送信するのをスキップします（デバッグ用、通常は `return_all=true` と一緒に使用されます）。
  * `conversation`: 会話履歴を表す `AbstractMessage` オブジェクトのオプションベクトル。現在、許可されていません。
  * `http_kwargs`: HTTPキーワード引数の名前付きタプル。
  * `api_kwargs`: APIキーワード引数の名前付きタプル。以下にいくつかの重要な引数を強調します：

      * `response_format`: 画像が返されるフォーマット。 "url" または "b64_json" のいずれかです。デフォルトは "url"（リンクは60分後に無効になります）。
      * `style`: 生成された画像のスタイル（DALL-E 3のみ）。 "vidid" または "natural" のいずれかです。デフォルトは "vidid"。
  * `kwargs`: プロンプト/テンプレートを埋めるために使用されるプロンプト変数

# 戻り値

`return_all=false`（デフォルト）の場合：

  * `msg`: 生成された1つ以上の画像を表す `DataMessage` オブジェクト。関連する場合は書き直されたプロンプト、ステータス、経過時間を含みます。

抽出された文字列にアクセスするには `msg.content` を使用します。

`return_all=true` の場合：

  * `conversation`: AIモデルからの応答（`AIMessage`）を含む、完全な会話履歴を表す `AbstractMessage` オブジェクトのベクトル。

また、`ai_str`、`aai_str`、`aigenerate`、`aiembed`、`aiclassify`、`aiextract`、`aiscan`、`aitemplates` も参照してください。

# 注意事項

  * この関数はマルチターンの会話をサポートしていません（つまり、`conversation` 引数を介して以前の会話を提供しないでください）。
  * APIによってトークン追跡は提供されていないため、メッセージはコストを報告しませんが、実際にはお金がかかります！
  * URLベースの画像は60分以内にダウンロードする必要があります。リンクは無効になります。

# 例

画像を生成する：

```julia
# `image_size`、`image_quality` kwargs で実験できます！
msg = aiimage("A white cat on a car")

# 画像をファイルにダウンロードする
using Downloads
Downloads.download(msg.content[:url], "cat_on_car.png")

# DALL-E 3 が使用した修正されたプロンプトも見ることができます
msg.content[:revised_prompt]
# 出力: "Visualize a pristine white cat gracefully perched atop a shiny car. 
# The cat's fur is stark white and its eyes bright with curiosity. 
# As for the car, it could be a contemporary sedan, glossy and in a vibrant color. 
# The scene could be set under the blue sky, enhancing the contrast between the white cat, the colorful car, and the bright blue sky."
```

URLベースの画像は60分以内にダウンロードする必要があります。リンクは無効になります。

データメッセージに直接画像をダウンロードしたい場合は、`api_kwargs` に `response_format="b64_json"` を指定してください：

```julia
msg = aiimage("A white cat on a car"; image_quality="hd", api_kwargs=(; response_format="b64_json"))

# 次に、Base64パッケージを使用してデコードし、ファイルに保存する必要があります：
using Base64
write("cat_on_car_hd.png", base64decode(msg.content[:b64_json]));
```
