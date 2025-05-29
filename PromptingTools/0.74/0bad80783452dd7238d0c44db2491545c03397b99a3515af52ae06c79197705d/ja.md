```
aigenerate(prompt_schema::AbstractOllamaManagedSchema, prompt::ALLOWED_PROMPT_TYPE; verbose::Bool = true,
    api_key::String = "", model::String = MODEL_CHAT,
    return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    streamcallback::Any = nothing,
    http_kwargs::NamedTuple = NamedTuple(), api_kwargs::NamedTuple = NamedTuple(),
    kwargs...)
```

与えられたプロンプトに基づいてAIの応答を生成します。OpenAI APIを使用します。

# 引数

  * `prompt_schema`: 適用すべきプロンプトテンプレートを指定するためのオプションオブジェクト（デフォルトは `PROMPT_SCHEMA = OpenAISchema`、`AbstractManagedSchema`ではありません）
  * `prompt`: AIの会話のためのプロンプトを表す文字列、`UserMessage`、`AbstractMessage`のベクター、または`AITemplate`であることができます
  * `verbose`: 追加情報を印刷するかどうかを示すブール値。
  * `api_key`: インターフェースの一貫性のために提供されます。ローカルホストのOllamaには必要ありません。
  * `model`: 応答を生成するために使用するモデルを表す文字列。`MODEL_ALIASES`で定義されたモデルIDに対応するエイリアスであることができます。
  * `return_all::Bool=false`: `true`の場合、会話の全履歴を返します。そうでない場合は、最後のメッセージ（`AIMessage`）のみを返します。
  * `dry_run::Bool=false`: `true`の場合、メッセージをモデルに送信するのをスキップします（デバッグ用、通常は`return_all=true`と一緒に使用されます）。
  * `conversation::AbstractVector{<:AbstractMessage}=[]`: このスキーマでは許可されていません。互換性のためにのみ提供されています。
  * `streamcallback`: ストリーミング応答を処理するためのコールバック関数。単に`stdout`または`StreamCallback`オブジェクトであることができます。詳細は`?StreamCallback`を参照してください。
  * `http_kwargs::NamedTuple`: HTTPリクエストのための追加のキーワード引数。デフォルトは空の`NamedTuple`です。
  * `api_kwargs::NamedTuple`: Ollama APIのための追加のキーワード引数。デフォルトは空の`NamedTuple`です。
  * `kwargs`: プロンプト/テンプレートを埋めるために使用されるプロンプト変数

# 戻り値

  * `msg`: 生成されたAIメッセージを表す`AIMessage`オブジェクトで、内容、ステータス、トークン、経過時間を含みます。

抽出された文字列にアクセスするには`msg.content`を使用します。

参照: `ai_str`, `aai_str`, `aiembed`

# 例

APIをテストするためのシンプルなハローワールド：

```julia
const PT = PromptingTools
schema = PT.OllamaSchema() # Ollamaを使用したい場合は明示的に指定する必要があります。OpenAISchemaがデフォルトです。

msg = aigenerate(schema, "Say hi!"; model="openhermes2.5-mistral")
# [ Info: Tokens: 69 in 0.9 seconds
# AIMessage("Hello! How can I assist you today?")
```

`msg`は`AIMessage`オブジェクトです。生成された文字列には`content`プロパティを介してアクセスします：

```julia
typeof(msg) # AIMessage{SubString{String}}
propertynames(msg) # (:content, :status, :tokens, :elapsed
msg.content # "Hello! How can I assist you today?"
```

注意: 使用したいスキーマについて明示的に指定する必要があります。指定しない場合、デフォルトで`OpenAISchema`（=`PT.DEFAULT_SCHEMA`）になります。___ 文字列補間を使用できます：

```julia
const PT = PromptingTools
schema = PT.OllamaSchema()
a = 1
msg=aigenerate(schema, "What is `$a+$a`?"; model="openhermes2.5-mistral")
msg.content # "The result of `1+1` is `2`."
```

___ 会話全体やより複雑なプロンプトを`Vector{AbstractMessage}`として提供できます：

```julia
const PT = PromptingTools
schema = PT.OllamaSchema()

conversation = [
    PT.SystemMessage("You're master Yoda from Star Wars trying to help the user become a Yedi."),
    PT.UserMessage("I have feelings for my iPhone. What should I do?")]

msg = aigenerate(schema, conversation; model="openhermes2.5-mistral")
# [ Info: Tokens: 111 in 2.1 seconds
# AIMessage("Strong the attachment is, it leads to suffering it may. Focus on the force within you must, ...<continues>")
```

ストリーミングを追加するには、`streamcallback`引数を使用します。

```julia
msg = aigenerate("Count from 1 to 10."; streamcallback = stdout)
```

または、より多くの制御を持ちたい場合は、`StreamCallback`オブジェクトを使用します。

```julia
streamcallback = PT.StreamCallback()
msg = aigenerate("Count from 1 to 10."; streamcallback)
```

警告: `flavor`を持つ`StreamCallback`オブジェクトを提供する場合、すべてを自分で設定したいと仮定しますので、`api_kwargs`で`stream = true`を設定する必要があります！

```julia
streamcallback = PT.StreamCallback(; flavor = PT.OllamaStream())
msg = aigenerate("Count from 1 to 10."; streamcallback, api_kwargs = (; stream = true))
```
