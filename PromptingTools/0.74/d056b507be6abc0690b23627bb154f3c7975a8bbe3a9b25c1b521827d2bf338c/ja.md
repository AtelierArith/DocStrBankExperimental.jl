```
aiextract(prompt_schema::AbstractAnthropicSchema, prompt::ALLOWED_PROMPT_TYPE;
    return_type::Union{Type, AbstractTool, Vector},
    verbose::Bool = true,
    api_key::String = ANTHROPIC_API_KEY,
    model::String = MODEL_CHAT,
    return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    no_system_message::Bool = false,
    http_kwargs::NamedTuple = (retry_non_idempotent = true,
        retries = 5,
        readtimeout = 120), api_kwargs::NamedTuple = NamedTuple(),
    cache::Union{Nothing, Symbol} = nothing,
    betas::Union{Nothing, Vector{Symbol}} = nothing,
    kwargs...)
```

提供されたプロンプトから必要な情報（**`return_type`**で定義された構造体によって）を抽出するために、Anthropicの関数呼び出しモードを活用します。

これは、テキストから構造化された情報を抽出するための完璧なソリューションです（例：ニュース記事の組織名を抽出するなど）。

ベストプラクティスについては[こちら](https://docs.anthropic.com/claude/docs/tool-use#tool-use-best-practices-and-limitations)をお読みください。

これは、`aigenerate`呼び出しの軽量ラッパーであり、追加のキーワード引数`return_type`を提供する必要があり、モデルの出力がそれに従うように強制します。

# 引数

  * `prompt_schema`: 適用すべきプロンプトテンプレートを指定するためのオプションオブジェクト（デフォルトは`PROMPT_SCHEMA = OpenAISchema`）
  * `prompt`: AIとの会話のためのプロンプトを表す文字列、`UserMessage`、`AbstractMessage`のベクター、または`AITemplate`である可能性があります。
  * `return_type`: 抽出したい情報を表す**構造体**の型。構造体のインスタンスを提供せず、型のみを提供してください。構造体にドキュメント文字列がある場合、それもモデルに提供されます。これは、構造化されたモデル出力を強制したり、より多くの情報を提供するために使用されます。あるいは、フィールド名とその型のベクターを提供することもできます（構文については`?generate_struct`関数を参照してください）。
  * `verbose`: 追加情報を印刷するかどうかを示すブール値。
  * `api_key`: OpenAI APIにアクセスするためのAPIキーを表す文字列。
  * `model`: 応答を生成するために使用するモデルを表す文字列。`MODEL_ALIASES`で定義されたモデルIDに対応するエイリアスである可能性があります。
  * `return_all::Bool=false`: `true`の場合、会話履歴全体を返し、そうでない場合は最後のメッセージ（`AIMessage`）のみを返します。
  * `dry_run::Bool=false`: `true`の場合、メッセージをモデルに送信するのをスキップします（デバッグ用、通常は`return_all=true`と一緒に使用されます）。
  * `conversation`: 会話履歴を表す`AbstractMessage`オブジェクトのオプションベクター。提供されない場合は、空のベクターとして初期化されます。
  * `no_system_message::Bool = false`: `true`の場合、会話履歴のシステムメッセージをスキップします。
  * `http_kwargs`: HTTPキーワード引数の名前付きタプル。
  * `api_kwargs`: APIキーワード引数の名前付きタプル。

      * `:tool_choice`: 使用するツールを示す文字列。サポートされている値は`nothing`、`"auto"`、`"any"`、および`"exact"`です。`nothing`はデフォルトのツール選択を使用します。
  * `cache`: 使用するキャッシング戦略を表すシンボル。現在サポートされているのは`nothing`（キャッシングなし）、`:system`、`:tools`、`:last`、`:all_but_last`、および`:all`のみです。注意：コスト見積もりは誤っている可能性があります（キャッシングを無視します）。

      * `:system`: システムメッセージのみをキャッシュ可能としてマークします。大きなシステムメッセージがあり、短い会話（返信なし/マルチターン会話）を送信する場合の最良のデフォルトです。
      * `:all`: システム、最後から1つ前のユーザーメッセージ、および最後のユーザーメッセージをキャッシュ可能としてマークします。マルチターン会話に最適です（キャッシュポイントを「最後」として書き込み、次のターンで「前の」キャッシュマークとして読み取ります）。
      * `:last`: 最後のメッセージのみをキャッシュ可能としてマークします。同じリクエストを複数回送信したい場合（最後のユーザーメッセージまで保存したい場合）のみ使用します。これはマルチターン会話には機能しません。なぜなら「最後」のメッセージは常に移動するからです。
      * `:all_but_last`: システムと最後から1つ前のユーザーメッセージをマークします。再利用したいが続行しない長い会話がある場合に使用します（その後のメッセージ/フォローアップはありません）。
      * 簡単に言えば、マルチターン会話には`:all`を、同じシステムメッセージを持つ繰り返しの単一ターン会話には`:system`を、再利用したいが続行しない長い会話には`:all_but_last`を使用します。
  * `betas::Union{Nothing, Vector{Symbol}}`: 使用するベータ機能を表すシンボルのベクター。詳細については`?anthropic_extra_headers`を参照してください。
  * `kwargs`: プロンプト/テンプレートを埋めるために使用されるプロンプト変数

注意：現時点では、キャッシュは1024トークンを超えるプロンプトセグメントにのみ許可されています（場合によっては2048トークンを超えることもあります）。短いプロンプトをキャッシュしようとするとエラーが発生します。

# 戻り値

`return_all=false`（デフォルト）の場合：

  * `msg`: 抽出されたデータを表す`DataMessage`オブジェクトで、内容、ステータス、トークン、および経過時間が含まれます。抽出されたデータにアクセスするには`msg.content`を使用します。

`return_all=true`の場合：

  * `conversation`: AIモデルからの応答（`DataMessage`）を含む、完全な会話履歴を表す`AbstractMessage`オブジェクトのベクター。

`tool_call_signature`、`MaybeExtract`、`ItemsExtract`、`aigenerate`も参照してください。

# 例

年齢、体重、高さなどの特定の測定値をテキストから抽出したいですか？必要な情報を構造体（`return_type`）として定義する必要があります：

```
"Person's age, height, and weight."
struct MyMeasurement
    age::Int # 必須
    height::Union{Int,Nothing} # オプション
    weight::Union{Nothing,Float64} # オプション
end
msg = aiextract("James is 30, weighs 80kg. He's 180cm tall."; model="claudeh", return_type=MyMeasurement)
# PromptingTools.DataMessage(MyMeasurement)
msg.content
# MyMeasurement(30, 180, 80.0)
```

`Nothing`を許可するフィールドは、スキーマでオプションとしてマークされています：

```
msg = aiextract("James is 30."; model="claudeh", return_type=MyMeasurement)
# MyMeasurement(30, nothing, nothing)
```

複数のアイテムを抽出したい場合は、ラッパー構造体を定義して`MyMeasurement`のベクターを取得します：

```
struct ManyMeasurements
    measurements::Vector{MyMeasurement}
end

msg = aiextract("James is 30, weighs 80kg. He's 180cm tall. Then Jack is 19 but really tall - over 190!"; model="claudeh", return_type=ManyMeasurements)

msg.content.measurements
# 2-element Vector{MyMeasurement}:
#  MyMeasurement(30, 180, 80.0)
#  MyMeasurement(19, 190, nothing)
```

または、便利なラッパー`ItemsExtract`を使用して複数の測定値を抽出できます（ゼロ、1つ、またはそれ以上）：

```julia
using PromptingTools: ItemsExtract

return_type = ItemsExtract{MyMeasurement}
msg = aiextract("James is 30, weighs 80kg. He's 180cm tall. Then Jack is 19 but really tall - over 190!"; model="claudeh", return_type)

msg.content.items # 抽出されたアイテムを確認
```

データが見つからない場合に抽出が優雅に失敗するようにしたい場合は、`MaybeExtract{T}`ラッパーを使用します（このトリックはInstructorパッケージからインスパイアを受けています！）：

```
using PromptingTools: MaybeExtract

return_type = MaybeExtract{MyMeasurement}
# 実質的には同じです：
# struct MaybeExtract{T}
#     result::Union{T, Nothing} // 抽出の結果
#     error::Bool // 結果が見つかった場合はtrue、そうでない場合はfalse
#     message::Union{Nothing, String} // 結果が見つからない場合のみ存在し、短く簡潔であるべき
# end

# LLMの抽出が失敗した場合、結果の代わりに`error`と`message`フィールドを持つDictが返されます！
msg = aiextract("Extract measurements from the text: I am giraffe"; model="claudeo", return_type)
msg.content
# 出力: MaybeExtract{MyMeasurement}(nothing, true, "I'm sorry, but your input of "I am giraffe" does not contain any information about a person's age, height or weight measurements that I can extract. To use this tool, please provide a statement that includes at least the person's age, and optionally their height in inches and weight in pounds. Without that information, I am unable to extract the requested measurements.")
```

このようにして、エラーを優雅に処理し、抽出が失敗した理由を取得できます（`msg.content.message`に）。

ただし、これは`claudeh`のような弱いモデルでは失敗する可能性があるため、埋め込み推論ステップを持つプロンプトテンプレートのいくつかを適用できます：

```julia
msg = aiextract(:ExtractDataCoTXML; data="I am giraffe", model="claudeh", return_type)
msg.content
# 出力: MaybeExtract{MyMeasurement}(nothing, true, "The provided data does not contain the expected information about a person's age, height, and weight.")
```

プロンプトテンプレートを使用する際には、抽出のために対応するプレースホルダーとして`data`を提供することに注意してください（このテンプレートのドキュメントについては`aitemplates("extract")`を参照してください）。

エラーメッセージは、私たちの`MyMeasurement`のドキュメント文字列で人間のためのものであると述べたため、キリンが人間ではないことに言及しています！

`aiextract`を使用したフィールド名のベクターの例

```julia
fields = [:location, :temperature => Float64, :condition => String]
msg = aiextract("Extract the following information from the text: location, temperature, condition. Text: The weather in New York is sunny and 72.5 degrees Fahrenheit."; 
return_type = fields, model="claudeh")
```

または、単に`aiextract("some text"; return_type = [:reasoning,:answer], model="claudeh")`を呼び出して、抽出タスクのためのChain of Thought推論を取得します。

新しく生成された型として返され、`PromptingTools.isextracted(msg.content) == true`を使用してデータが正しく抽出されたことを確認できます。

この新しい構文では、フィールドレベルの説明を提供することも可能で、モデルに渡されます。

```julia
fields_with_descriptions = [
    :location,
    :temperature => Float64,
    :temperature__description => "Temperature in degrees Fahrenheit",
    :condition => String,
    :condition__description => "Current weather condition (e.g., sunny, rainy, cloudy)"
]
msg = aiextract("The weather in New York is sunny and 72.5 degrees Fahrenheit."; return_type = fields_with_descriptions, model="claudeh")
```
