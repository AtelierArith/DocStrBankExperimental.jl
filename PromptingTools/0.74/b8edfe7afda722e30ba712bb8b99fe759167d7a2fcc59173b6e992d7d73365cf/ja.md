```
aigenerate(prompt_schema::AbstractAnthropicSchema, prompt::ALLOWED_PROMPT_TYPE; verbose::Bool = true,
    api_key::String = ANTHROPIC_API_KEY, model::String = MODEL_CHAT,
    return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    streamcallback::Any = nothing,
    no_system_message::Bool = false,
    aiprefill::Union{Nothing, AbstractString} = nothing,
    http_kwargs::NamedTuple = NamedTuple(), api_kwargs::NamedTuple = NamedTuple(),
    cache::Union{Nothing, Symbol} = nothing,
    betas::Union{Nothing, Vector{Symbol}} = nothing,
    kwargs...)
```

与えられたプロンプトに基づいてAIの応答を生成します。Anthropic APIを使用します。

# 引数

  * `prompt_schema`: 適用すべきプロンプトテンプレートを指定するためのオプションオブジェクト（デフォルトは `PROMPT_SCHEMA = OpenAISchema`、`AbstractAnthropicSchema`ではありません）
  * `prompt`: AIの会話のためのプロンプトを表す文字列、`UserMessage`、`AbstractMessage`のベクター、または`AITemplate`であることができます。
  * `verbose`: 追加情報を印刷するかどうかを示すブール値。
  * `api_key`: Anthropic APIのAPIキー。デフォルトは `ANTHROPIC_API_KEY`（`ENV["ANTHROPIC_API_KEY"]`を介して読み込まれます）。
  * `model`: 応答を生成するために使用するモデルを表す文字列。`MODEL_ALIASES`で定義されたモデルIDに対応するエイリアスであることができます。例: "claudeh"。
  * `return_all::Bool=false`: `true`の場合、会話の全履歴を返します。それ以外の場合は最後のメッセージ（`AIMessage`）のみを返します。
  * `dry_run::Bool=false`: `true`の場合、モデルにメッセージを送信するのをスキップします（デバッグ用、通常は`return_all=true`と一緒に使用されます）。
  * `conversation::AbstractVector{<:AbstractMessage}=[]`: このスキーマでは許可されていません。互換性のために提供されています。
  * `streamcallback::Any`: ストリーミング応答を処理するためのコールバック関数。単に`stdout`または`StreamCallback`オブジェクトであることができます。詳細は`?StreamCallback`を参照してください。注意: `flavor`を指定しない限り、`StreamCallback`（および必要な`api_kwargs`）を設定します。詳細は`?configure_callback!`を参照してください。
  * `no_system_message::Bool=false`: `true`の場合、会話履歴にデフォルトのシステムメッセージを含めないか、提供されたシステムメッセージをユーザーメッセージに変換します。
  * `aiprefill::Union{Nothing, AbstractString}`: AIの応答のプレフィルとして使用される文字列。この文字列はAIの応答を特定の方向に導き（出力トークンを節約する可能性があります）、末尾にスペースを含めてはいけません。JSONフォーマットに便利です。
  * `http_kwargs::NamedTuple`: HTTPリクエストのための追加のキーワード引数。デフォルトは空の`NamedTuple`です。
  * `api_kwargs::NamedTuple`: Ollama APIのための追加のキーワード引数。デフォルトは空の`NamedTuple`です。

      * `max_tokens::Int`: 生成するトークンの最大数。デフォルトは2048で、APIの必須パラメータです。
  * `cache`: 使用するキャッシング戦略を表すシンボル。現在、`nothing`（キャッシングなし）、`:system`、`:tools`、`:last`、`:all_but_last`、および`:all`のみがサポートされています。キャッシングを無視するため、コスト見積もりが間違っていることに注意してください。

      * `:system`: システムメッセージのみをキャッシュ可能としてマークします。大きなシステムメッセージがあり、短い会話（返信なし/マルチターン会話）を送信する場合の最良のデフォルトです。
      * `:all`: SYSTEM、最後から1つ前のユーザーメッセージ、および最後のユーザーメッセージをキャッシュ可能としてマークします。マルチターン会話に最適です（キャッシュポイントを「最後」として書き込み、次のターンで「前の」キャッシュマークとして読み取られます）。
      * `:last`: 最後のメッセージのみをキャッシュ可能としてマークします。同じリクエストを複数回送信したい場合（最後のユーザーメッセージまで保存したい場合）のみ使用します。これはマルチターン会話には機能しません。「最後」のメッセージは常に移動します。
      * `:all_but_last`: SYSTEMと最後から1つ前のユーザーメッセージをマークします。再利用したいが続行しない長い会話がある場合に使用します（その後のメッセージ/フォローアップなし）。
      * 短く言えば、マルチターン会話には`:all`を、同じシステムメッセージを持つ繰り返しの単一ターン会話には`:system`を、再利用したいが続行しない長い会話には`:all_but_last`を使用します。
  * `betas::Union{Nothing, Vector{Symbol}}`: 使用するベータ機能を表すシンボルのベクター。詳細は`?anthropic_extra_headers`を参照してください。
  * `kwargs`: プロンプト/テンプレートを埋めるために使用されるプロンプト変数

注意: 現在、キャッシュは1024トークンを超えるプロンプトセグメントにのみ許可されています（場合によっては2048トークンを超える）。短いプロンプトをキャッシュしようとするとエラーが発生します。

# 戻り値

  * `msg`: 生成されたAIメッセージを表す`AIMessage`オブジェクトで、内容、ステータス、トークン、および経過時間を含みます。

`msg.content`を使用して抽出された文字列にアクセスします。

また、`ai_str`、`aai_str`も参照してください。

# 例

APIをテストするためのシンプルなハローワールド：

```julia
const PT = PromptingTools
schema = PT.AnthropicSchema() # Anthropicを使用したい場合は明示的に指定する必要があります。そうでない場合、OpenAISchemaがデフォルトです。

msg = aigenerate(schema, "Say hi!"; model="claudeh") #claudehはClaude 3 Haikuのモデルエイリアスで、速くて安価なモデルです。
[ Info: Tokens: 21 @ Cost: $0.0 in 0.6 seconds
AIMessage("Hello!")
```

`msg`は`AIMessage`オブジェクトです。生成された文字列には`content`プロパティを介してアクセスします：

```julia
typeof(msg) # AIMessage{SubString{String}}
propertynames(msg) # (:content, :status, :tokens, :elapsed, :cost, :log_prob, :finish_reason, :run_id, :sample_id, :_type)
msg.content # "Hello!
```

注意: 使用したいスキーマについて明示的に指定する必要があります。指定しない場合、デフォルトは`OpenAISchema`（=`PT.DEFAULT_SCHEMA`）になります。あるいは、既知のモデル名やエイリアス（例: `claudeh`はClaude 3 Haiku - `MODEL_REGISTRY`を参照）を提供すると、スキーマはモデル名から推測されます。

次の例ではClaude 3 Haikuモデルを使用するので、スキーマを指定する必要はありません。他のClaude 3モデルについては「claudeo」や「claudes」も参照してください。

文字列補間を使用できます：

```julia
const PT = PromptingTools

a = 1
msg=aigenerate("What is `$a+$a`?"; model="claudeh")
msg.content # "The answer to `1+1` is `2`."
```

___ 会話全体やより複雑なプロンプトを`Vector{AbstractMessage}`として提供できます。Claudeモデルは`AIMessage`で終了した会話を完了するのが得意です（彼らは単にそこから続けます）：

```julia
const PT = PromptingTools

conversation = [
    PT.SystemMessage("You're master Yoda from Star Wars trying to help the user become a Yedi."),
    PT.UserMessage("I have feelings for my iPhone. What should I do?"),
    PT.AIMessage("Hmm, strong the attachment is,")]

msg = aigenerate(conversation; model="claudeh")
AIMessage("I sense. But unhealthy it may be. Your iPhone, a tool it is, not a living being. Feelings of affection, understandable they are, <continues>")
```

ストリーミングの例：

```julia
# 最も簡単な使用法、テキストをストリームする場所を提供するだけ
msg = aigenerate("Count from 1 to 100."; streamcallback = stdout, model="claudeh")

streamcallback = PT.StreamCallback()
msg = aigenerate("Count from 1 to 100."; streamcallback, model="claudeh")
# これにより、`streamcallback.chunks`で各チャンクを検査できます。繰り返し呼び出しの間に`empty!(streamcallback)`でそれを空にすることができます。

# 各チャンクの詳細を含む冗長な出力を取得
streamcallback = PT.StreamCallback(; verbose=true, throw_on_error=true)
msg = aigenerate("Count from 1 to 10."; streamcallback, model="claudeh")
```

注意: ストリーミングサポートはAnthropicモデルのみに対応しており、ツール呼び出しやいくつかの他の機能（logprobs、拒否など）にはまだ対応していません。

AIの応答のプレフィルを提供して、応答を特定の方向に導くこともできます（例: フォーマット、スタイル）：

```julia
msg = aigenerate("Sum up 1 to 100."; aiprefill = "I'd be happy to answer in one number without any additional text. The answer is:", model="claudeh")
```

注意: 末尾にスペースを含めてはいけません。そうするとAPIエラーが発生します。 ```
