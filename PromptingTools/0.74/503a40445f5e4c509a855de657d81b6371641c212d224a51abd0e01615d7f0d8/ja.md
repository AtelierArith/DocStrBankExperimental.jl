```
aiextract(prompt_schema::AbstractOpenAISchema, prompt::ALLOWED_PROMPT_TYPE;
    return_type::Union{Type, AbstractTool, Vector},
    verbose::Bool = true,
    api_key::String = OPENAI_API_KEY,
    model::String = MODEL_CHAT,
    return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    http_kwargs::NamedTuple = (retry_non_idempotent = true,
        retries = 5,
        readtimeout = 120), api_kwargs::NamedTuple = (;
        tool_choice = nothing),
    strict::Union{Nothing, Bool} = nothing,
    kwargs...)
```

提供されたプロンプトから必要な情報（**`return_type`**で定義された構造体によって定義される）をOpenAIの関数呼び出しモードを利用して抽出します。

これは、テキストから構造化された情報を抽出するための完璧なソリューションです（例：ニュース記事の組織名を抽出するなど）。

これは、`aigenerate`呼び出しの軽いラッパーであり、追加のキーワード引数`return_type`を提供する必要があり、モデルの出力がそれに従うように強制します。

!!! 注意: 型は具体的でなければなりません。これにより、JSONスキーマへの正しい変換と、その後の構造体への変換が助けられます。

# 引数

  * `prompt_schema`: 適用すべきプロンプトテンプレートを指定するためのオプションオブジェクト（デフォルトは`PROMPT_SCHEMA = OpenAISchema`）
  * `prompt`: AIとの会話のためのプロンプトを表す文字列、`UserMessage`、`AbstractMessage`のベクター、または`AITemplate`である可能性があります
  * `return_type`: 抽出したい情報を表す**構造体**の型（またはツール、型のベクター）。構造体のインスタンスを提供せず、型のみを提供してください。あるいは、フィールド名とその型のベクターを提供することもできます（構文については`?generate_struct`関数を参照）。構造体にドキュメント文字列がある場合、それもモデルに提供されます。これは、構造化されたモデル出力を強制したり、より多くの情報を提供するために使用されます。
  * `verbose`: 追加情報を印刷するかどうかを示すブール値。
  * `api_key`: OpenAI APIにアクセスするためのAPIキーを表す文字列。
  * `model`: 応答を生成するために使用するモデルを表す文字列。`MODEL_ALIASES`で定義されたモデルIDに対応するエイリアスである可能性があります。
  * `return_all::Bool=false`: `true`の場合、会話の全履歴を返し、そうでない場合は最後のメッセージ（`AIMessage`）のみを返します。
  * `dry_run::Bool=false`: `true`の場合、モデルにメッセージを送信するのをスキップします（デバッグ用、通常は`return_all=true`と一緒に使用されます）。
  * `conversation`: 会話履歴を表す`AbstractMessage`オブジェクトのオプションベクター。提供されない場合は、空のベクターとして初期化されます。
  * `http_kwargs`: HTTPキーワード引数の名前付きタプル。
  * `api_kwargs`: APIキーワード引数の名前付きタプル。

      * `tool_choice`: API呼び出しに使用するツールを指定します。通常は「auto」、「any」、「exact」のいずれかです。`nothing`はデフォルトを選択します。1つのツールの場合は「exact」、複数のツールの場合は「auto」にデフォルト設定されており、これは1つの正確な関数を強制するための架空の値です。Mistral、Togetherなどのプロバイダーは、代わりに「any」を使用します。
  * `strict::Union{Nothing, Bool} = nothing`: 応答の厳密な生成を強制するかどうかを示すブール値（OpenAIモデルのみサポート）。最初のリクエストには追加のレイテンシがあります。`nothing`の場合、標準の関数呼び出しが使用されます。
  * `json_mode::Union{Nothing, Bool} = nothing`: `json_mode = true`の場合、応答にJSONモードを使用します（OpenAIモデルのみサポート）。`nothing`の場合、標準の関数呼び出しが使用されます。JSONモードは、関数呼び出しモードではなく、特定の出力形式（JSONなど）を強制したい場合に便利です。最初のリクエストには数秒の遅延が予想されます。
  * `kwargs`: プロンプト/テンプレートを埋めるために使用されるプロンプト変数

# 戻り値

`return_all=false`（デフォルト）の場合：

  * `msg`: 抽出されたデータを表す`DataMessage`オブジェクトで、コンテンツ、ステータス、トークン、経過時間が含まれます。抽出されたデータにアクセスするには`msg.content`を使用します。

`return_all=true`の場合：

  * `conversation`: AIモデルからの応答（`DataMessage`）を含む、会話履歴全体を表す`AbstractMessage`オブジェクトのベクター。

注意: `msg.content`は、単一のツールが使用されている場合は単一のオブジェクトであり、複数のツールが使用されている場合はオブジェクトのベクターである可能性があります！

他にも: `tool_call_signature`、`MaybeExtract`、`ItemsExtract`、`aigenerate`、`generate_struct`

# 例

年齢、体重、高さなどの特定の測定値をテキストから抽出したいですか？必要な情報を構造体（`return_type`）として定義する必要があります：

```
"Person's age, height, and weight."
struct MyMeasurement
    age::Int # 必須
    height::Union{Int,Nothing} # オプション
    weight::Union{Nothing,Float64} # オプション
end
msg = aiextract("James is 30, weighs 80kg. He's 180cm tall."; return_type=MyMeasurement)
# PromptingTools.DataMessage(MyMeasurement)
msg.content
# MyMeasurement(30, 180, 80.0)
```

`Nothing`を許可するフィールドは、スキーマでオプションとしてマークされています：

```
msg = aiextract("James is 30."; return_type=MyMeasurement)
# MyMeasurement(30, nothing, nothing)
```

複数のアイテムを抽出したい場合は、`MyMeasurement`のベクターを取得するためのラッパー構造体を定義します：

```
struct ManyMeasurements
    measurements::Vector{MyMeasurement}
end

msg = aiextract("James is 30, weighs 80kg. He's 180cm tall. Then Jack is 19 but really tall - over 190!"; return_type=ManyMeasurements)

msg.content.measurements
# 2-element Vector{MyMeasurement}:
#  MyMeasurement(30, 180, 80.0)
#  MyMeasurement(19, 190, nothing)
```

または、便利なラッパー`ItemsExtract`を使用して、複数の測定値を抽出することもできます（ゼロ、1つ、またはそれ以上）：

```julia
using PromptingTools: ItemsExtract

return_type = ItemsExtract{MyMeasurement}
msg = aiextract("James is 30, weighs 80kg. He's 180cm tall. Then Jack is 19 but really tall - over 190!"; return_type)

msg.content.items # 抽出されたアイテムを確認
```

データが見つからない場合に抽出が優雅に失敗するようにしたい場合は、`MaybeExtract{T}`ラッパーを使用します（このトリックはInstructorパッケージからインスパイアされています！）：

```
using PromptingTools: MaybeExtract

return_type = MaybeExtract{MyMeasurement}
# 実質的には次のようになります：
# struct MaybeExtract{T}
#     result::Union{T, Nothing} // 抽出の結果
#     error::Bool // 結果が見つかった場合はtrue、そうでない場合はfalse
#     message::Union{Nothing, String} // 結果が見つからない場合のみ存在し、短く簡潔であるべき
# end

# LLM抽出が失敗した場合、結果の代わりに`error`と`message`フィールドを持つDictが返されます！
msg = aiextract("Extract measurements from the text: I am giraffe"; return_type)
msg.content
# MaybeExtract{MyMeasurement}(nothing, true, "I'm sorry, but I can only assist with human measurements.")
```

その方法で、エラーを優雅に処理し、抽出が失敗した理由を取得できます（`msg.content.message`に）。

エラーメッセージは、私たちの`MyMeasurement`のドキュメント文字列で人間のためのものであると言ったため、キリンが人間ではないことを指しています！

一部の非OpenAIプロバイダーは、OpenAIとは異なる「ツール選択」の仕様を必要とします。たとえば、Mistralモデル（「mistrall」はmistral largeのため）を使用するには、次のようにします：

```julia
"Some fruit"
struct Fruit
    name::String
end
aiextract("I ate an apple",return_type=Fruit,api_kwargs=(;tool_choice="any"),model="mistrall")
# 2つの違いに注意してください：1）構造体にはドキュメント文字列が必要、2）tool_choiceが明示的に「any」に設定されています
```

`aiextract`を使用したフィールド名のベクターの例

```julia
fields = [:location, :temperature => Float64, :condition => String]
msg = aiextract("Extract the following information from the text: location, temperature, condition. Text: The weather in New York is sunny and 72.5 degrees Fahrenheit."; return_type = fields)
```

または、単に`aiextract("some text"; return_type = [:reasoning,:answer])`を呼び出して、抽出タスクのためのChain of Thought推論を取得します。

新しく生成された型で返され、`PromptingTools.isextracted(msg.content) == true`を使用してデータが正しく抽出されたことを確認できます。

この新しい構文では、フィールドレベルの説明を提供することもでき、それがモデルに渡されます。

```julia
fields_with_descriptions = [
    :location,
    :temperature => Float64,
    :temperature__description => "Temperature in degrees Fahrenheit",
    :condition => String,
    :condition__description => "Current weather condition (e.g., sunny, rainy, cloudy)"
]
msg = aiextract("The weather in New York is sunny and 72.5 degrees Fahrenheit."; return_type = fields_with_descriptions)
```

抽出が十分に賢く/創造的でないと感じた場合は、`json_mode = true`を使用してJSONモードを強制し、構造化された出力モードを自動的に有効にします（関数呼び出しモードとは対照的に）。

JSONモードは、特定の出力形式（JSONなど）を強制したい場合に便利で、モデルにその形式に従うようにしたいが、「関数呼び出し」であるふりをしたくない場合に役立ちます。特定の構造体に対して最初の呼び出しには数秒の遅延が予想されます。プロバイダーは最初に制約された文法を生成する必要があります。

```julia
msg = aiextract("Extract the following information from the text: location, temperature, condition. Text: The weather in New York is sunny and 72.5 degrees Fahrenheit."; 
return_type = fields_with_descriptions, json_mode = true)
# PromptingTools.DataMessage(NamedTuple)

msg.content
# (location = "New York", temperature = 72.5, condition = "sunny")
```

構造体を戻り値として提供する場合でも同様に機能します：

```julia
msg = aiextract("James is 30, weighs 80kg. He's 180cm tall."; return_type=MyMeasurement, json_mode=true)
```
