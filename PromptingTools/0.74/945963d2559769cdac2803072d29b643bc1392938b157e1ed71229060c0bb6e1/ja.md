```
aigenerate(prompt_schema::AbstractGoogleSchema, prompt::ALLOWED_PROMPT_TYPE;
    verbose::Bool = true,
    api_key::String = GOOGLE_API_KEY,
    model::String = "gemini-pro", return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    no_system_message::Bool = false,
    http_kwargs::NamedTuple = (retry_non_idempotent = true,
        retries = 5,
        readtimeout = 120), api_kwargs::NamedTuple = NamedTuple(),
    kwargs...)
```

与えられたプロンプトに基づいてAI応答を生成するために、Google Gemini APIを使用します。APIキーは[こちら](https://ai.google.dev/)で取得できます。

注意:

  * 2024年2月時点では「コスト」は報告されておらず、すべてのアクセスが無料のようです。詳細は[こちら](https://ai.google.dev/pricing)をご覧ください。
  * 返されたAIMessageの`tokens`は実際にはトークンではなく文字です。APIから提供されていないため、*保守的*な推定を使用しています。

# 引数

  * `prompt_schema`: 適用すべきプロンプトテンプレートを指定するためのオプションオブジェクト（デフォルトは`PROMPT_SCHEMA = OpenAISchema`）
  * `prompt`: AI会話のプロンプトを表す文字列、`UserMessage`、`AbstractMessage`のベクター、または`AITemplate`であることができます。
  * `verbose`: 追加情報を印刷するかどうかを示すブール値。
  * `api_key`: OpenAI APIにアクセスするためのAPIキーを表す文字列。
  * `model`: 応答生成に使用するモデルを表す文字列。`MODEL_ALIASES`で定義されたモデルIDに対応するエイリアスであることができます。デフォルトは
  * `return_all::Bool=false`: `true`の場合、会話の全履歴を返し、そうでない場合は最後のメッセージ（`AIMessage`）のみを返します。
  * `dry_run::Bool=false`: `true`の場合、モデルにメッセージを送信するのをスキップします（デバッグ用、通常は`return_all=true`と一緒に使用されます）。
  * `conversation`: 会話履歴を表す`AbstractMessage`オブジェクトのオプションベクター。提供されない場合は空のベクターとして初期化されます。
  * `no_system_message::Bool=false`: `true`の場合、会話履歴にデフォルトのシステムメッセージを含めないか、提供されたシステムメッセージをユーザーメッセージに変換します。
  * `http_kwargs`: HTTPキーワード引数の名前付きタプル。
  * `api_kwargs`: APIキーワード引数の名前付きタプル。
  * `kwargs`: プロンプト/テンプレートを埋めるために使用されるプロンプト変数

# 戻り値

`return_all=false`（デフォルト）の場合:

  * `msg`: 生成されたAIメッセージを表す`AIMessage`オブジェクトで、内容、ステータス、トークン、経過時間が含まれます。

抽出された文字列にアクセスするには`msg.content`を使用します。

`return_all=true`の場合:

  * `conversation`: AIモデルからの応答（`AIMessage`）を含む会話履歴を表す`AbstractMessage`オブジェクトのベクター。

また、`ai_str`、`aai_str`、`aiembed`、`aiclassify`、`aiextract`、`aiscan`、`aitemplates`も参照してください。

# 例

APIをテストするためのシンプルなハローワールド:

```julia
result = aigenerate("Say Hi!"; model="gemini-pro")
# AIMessage("Hi there! 👋 I'm here to help you with any questions or tasks you may have. Just let me know what you need, and I'll do my best to assist you.")
```

`result`は`AIMessage`オブジェクトです。生成された文字列には`content`プロパティを介してアクセスします:

```julia
typeof(result) # AIMessage{SubString{String}}
propertynames(result) # (:content, :status, :tokens, :elapsed
result.content # "Hi there! ...
```

___ 文字列補間とエイリアス「gemini」を使用できます:

```julia
a = 1
msg=aigenerate("What is `$a+$a`?"; model="gemini")
msg.content # "1+1 is 2."
```

___ 会話全体やより複雑なプロンプトを`Vector{AbstractMessage}`として提供できます:

```julia
const PT = PromptingTools

conversation = [
    PT.SystemMessage("You're master Yoda from Star Wars trying to help the user become a Yedi."),
    PT.UserMessage("I have feelings for my iPhone. What should I do?")]
msg=aigenerate(conversation; model="gemini")
# AIMessage("Young Padawan, you have stumbled into a dangerous path.... <continues>")
```
