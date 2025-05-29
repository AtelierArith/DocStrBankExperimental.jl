```
aigenerate(prompt_schema::AbstractOpenAISchema, prompt::ALLOWED_PROMPT_TYPE;
    verbose::Bool = true,
    api_key::String = OPENAI_API_KEY,
    model::String = MODEL_CHAT, return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    streamcallback::Any = nothing,
    no_system_message::Bool = false,
    name_user::Union{Nothing, String} = nothing,
    name_assistant::Union{Nothing, String} = nothing,
    http_kwargs::NamedTuple = (retry_non_idempotent = true,
        retries = 5,
        readtimeout = 120), api_kwargs::NamedTuple = NamedTuple(),
    kwargs...)
```

与えられたプロンプトに基づいてAIの応答を生成します。OpenAI APIを使用します。

# 引数

  * `prompt_schema`: 適用すべきプロンプトテンプレートを指定するためのオプションオブジェクト（デフォルトは `PROMPT_SCHEMA = OpenAISchema`）
  * `prompt`: AIの会話のためのプロンプトを表す文字列、`UserMessage`、`AbstractMessage`のベクター、または`AITemplate`であることができます。
  * `verbose`: 追加情報を印刷するかどうかを示すブール値。
  * `api_key`: OpenAI APIにアクセスするためのAPIキーを表す文字列。
  * `model`: 応答を生成するために使用するモデルを表す文字列。`MODEL_ALIASES`で定義されたモデルIDに対応するエイリアスであることができます。
  * `return_all::Bool=false`: `true`の場合、会話履歴全体を返します。そうでない場合は、最後のメッセージ（`AIMessage`）のみを返します。
  * `dry_run::Bool=false`: `true`の場合、メッセージをモデルに送信するのをスキップします（デバッグ用、通常は`return_all=true`と一緒に使用されます）。
  * `conversation`: 会話履歴を表す`AbstractMessage`オブジェクトのオプションベクター。提供されない場合は、空のベクターとして初期化されます。
  * `streamcallback`: ストリーミング応答を処理するためのコールバック関数。単に`stdout`または`StreamCallback`オブジェクトであることができます。詳細については`?StreamCallback`を参照してください。注意: `flavor`を指定しない限り、`StreamCallback`（および必要な`api_kwargs`）を設定します。詳細については`?configure_callback!`を参照してください。
  * `no_system_message::Bool=false`: `true`の場合、デフォルトのシステムメッセージは会話履歴に含まれません。既存のシステムメッセージは`UserMessage`に変換されます。
  * `name_user::Union{Nothing, String} = nothing`: 会話履歴でユーザーに使用する名前。デフォルトは`nothing`です。
  * `name_assistant::Union{Nothing, String} = nothing`: 会話履歴でアシスタントに使用する名前。デフォルトは`nothing`です。
  * `http_kwargs`: HTTPキーワード引数の名前付きタプル。
  * `api_kwargs`: APIキーワード引数の名前付きタプル。便利なパラメータには以下が含まれます：

      * `temperature`: サンプリングのための温度を表す浮動小数点数（すなわち、「創造性」の量）。通常は`0.7`にデフォルト設定されています。
      * `logprobs`: 各トークンの対数確率を返すかどうかを示すブール値。デフォルトは`false`です。
      * `n`: 一度に生成する完了の数を表す整数（サポートされている場合）。
      * `stop`: 会話の停止条件を表す文字列のベクター。デフォルトは空のベクターです。
  * `kwargs`: プロンプト/テンプレートを埋めるために使用されるプロンプト変数

# 戻り値

`return_all=false`（デフォルト）の場合：

  * `msg`: 生成されたAIメッセージを表す`AIMessage`オブジェクトで、内容、ステータス、トークン、経過時間が含まれます。

抽出された文字列にアクセスするには`msg.content`を使用します。

`return_all=true`の場合：

  * `conversation`: AIモデルからの応答（`AIMessage`）を含む会話履歴を表す`AbstractMessage`オブジェクトのベクター。

また、`ai_str`、`aai_str`、`aiembed`、`aiclassify`、`aiextract`、`aiscan`、`aitemplates`も参照してください。

# 例

APIをテストするためのシンプルなハローワールド：

```julia
result = aigenerate("Say Hi!")
# [ Info: Tokens: 29 @ Cost: $0.0 in 1.0 seconds
# AIMessage("Hello! How can I assist you today?")
```

`result`は`AIMessage`オブジェクトです。生成された文字列には`content`プロパティを介してアクセスします：

```julia
typeof(result) # AIMessage{SubString{String}}
propertynames(result) # (:content, :status, :tokens, :elapsed
result.content # "Hello! How can I assist you today?"
```

___ 文字列補間を使用できます：

```julia
a = 1
msg=aigenerate("What is `$a+$a`?")
msg.content # "The sum of `1+1` is `2`."
```

___ 会話全体やより複雑なプロンプトを`Vector{AbstractMessage}`として提供できます：

```julia
const PT = PromptingTools

conversation = [
    PT.SystemMessage("You're master Yoda from Star Wars trying to help the user become a Yedi."),
    PT.UserMessage("I have feelings for my iPhone. What should I do?")]
msg=aigenerate(conversation)
# AIMessage("Ah, strong feelings you have for your iPhone. A Jedi's path, this is not... <continues>")
```

ストリーミングの例：

```julia
# 最も簡単な使用法、テキストをストリームする場所を提供するだけ
msg = aigenerate("Count from 1 to 100."; streamcallback = stdout)

streamcallback = PT.StreamCallback()
msg = aigenerate("Count from 1 to 100."; streamcallback)
# これにより、`streamcallback.chunks`で各チャンクを検査できます。繰り返し呼び出しの間に`empty!(streamcallback)`でそれを空にすることができます。

# 各チャンクの詳細を含む冗長出力を取得
streamcallback = PT.StreamCallback(; verbose=true, throw_on_error=true)
msg = aigenerate("Count from 1 to 10."; streamcallback)
```

警告: `StreamCallback`オブジェクトを提供した場合、すべてを自分で設定したいと仮定しますので、`api_kwargs`で`stream = true`を設定する必要があります！

`?StreamCallback`で詳細を学びましょう。注意: ストリーミングサポートはOpenAIモデルのみに対応しており、ツール呼び出しやいくつかの他の機能（logprobs、拒否など）にはまだ対応していません。
