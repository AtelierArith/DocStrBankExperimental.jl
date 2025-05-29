```
aiclassify(prompt_schema::AbstractOpenAISchema, prompt::ALLOWED_PROMPT_TYPE;
    choices::AbstractVector{T} = ["true", "false", "unknown"],
    model::AbstractString = MODEL_CHAT,
    api_kwargs::NamedTuple = NamedTuple(),
    token_ids_map::Union{Nothing, Dict{<:AbstractString, <:Integer}} = nothing,
    kwargs...) where {T <: Union{AbstractString, Tuple{<:AbstractString, <:AbstractString}}}
```

与えられたプロンプト/ステートメントを任意の選択肢のリストに分類します。選択肢は文字列のベクターのみ、または選択肢と説明が提供される必要があります（タプルのベクター、つまり `("choice","description")`）。

これは「ルーティング」や類似のユースケースにとって迅速で簡単なオプションであり、ロジットバイアストリックを利用して1トークンのみを出力します。任意のカテゴリのリストに分類します（説明付きでも）。これは「ルーティング」や類似のユースケースにとって迅速で簡単なオプションであり、ロジットバイアストリックを利用しているため、1トークンのみを出力します。

!!! 注意: プロンプト/AITemplateには、エンコードされた選択肢で置き換えられるプレースホルダー `choices`（つまり `{{choices}}`）が必要です。

選択肢は列挙リストに書き換えられ、いくつかの既知のOpenAIトークンにマッピングされます（最大40の選択肢がサポートされています）。GPT3.5/4のトークンIDのマッピングは変数 `OPENAI_TOKEN_IDS` に保存されています。

これはロジットバイアストリックを使用し、出力を1トークンに制限してモデルにtrue/false/unknownのみを出力させるように強制します。このアイデアのクレジットは [AAAzzam](https://twitter.com/AAAzzam/status/1669753721574633473) にあります。

# 引数

  * `prompt_schema::AbstractOpenAISchema`: プロンプトのスキーマ。
  * `prompt`: `String`の場合は分類するプロンプト/ステートメント。`Symbol`の場合は、`render(schema,template)`を介してテンプレートとして展開されます。例: テンプレート `:JudgeIsItTrue` または `:InputClassifier`
  * `choices::AbstractVector{T}`: 分類される選択肢。文字列のベクターまたはタプルのベクターで、最初の要素が選択肢、2番目の要素が説明です。
  * `model::AbstractString = MODEL_CHAT`: 分類に使用するモデル。`MODEL_ALIASES`で定義されたモデルIDに対応するエイリアスである可能性があります。
  * `api_kwargs::NamedTuple = NamedTuple()`: API呼び出しのための追加のキーワード引数。
  * `token_ids_map::Union{Nothing, Dict{<:AbstractString, <:Integer}} = nothing`: カスタムトークンIDを対応する整数値にマッピングする辞書。`nothing`の場合、指定されたモデルのデフォルトトークンIDが使用されます。
  * `kwargs`: プロンプトテンプレートのための追加のキーワード引数。

# 例

ユーザー入力に基づいて、提供された2つのカテゴリのいずれかを選択します：

```julia
choices = ["animal", "plant"]
input = "Palm tree"
aiclassify(:InputClassifier; choices, input)
```

タプルとして提供された説明付きの選択肢：

```julia
choices = [("A", "any animal or creature"), ("P", "any plant or tree"), ("O", "anything else")]

# 以下の入力を試してください：
input = "spider" # -> "A"を返します（動物または生き物）
input = "daphodil" # -> "P"を返します（植物または木）
input = "castle" # -> "O"を返します（その他すべて）
aiclassify(:InputClassifier; choices, input)
```

この関数を使用して異なるエンドポイントへの質問をルーティングすることもできます（異なるテンプレートとプレースホルダーに注意してください）、例えば、

```julia
choices = [("A", "any question about animal or creature"), ("P", "any question about plant or tree"), ("O", "anything else")]
question = "how many spiders are there?"
msg = aiclassify(:QuestionRouter; choices, question)
# "A"
```

単純な真偽分類を使用することもできます：

```julia
aiclassify("Is two plus two four?") # true
aiclassify("Is two plus three a vegetable on Mars?") # false
```

`aiclassify`はtrue/false/unknownのみを返します。`tryparse`を使用して適切な`Bool`出力タイプを簡単に取得できます。例えば、

```julia
tryparse(Bool, aiclassify("Is two plus two four?")) isa Bool # true
```

`Nothing`型の出力は、モデルがステートメントをtrue/falseとして分類できなかったことを示します。

理想的には、より正確な応答を得るために役立つシステムプロンプトを再利用したいと考えています。このためにテンプレートがあります。例えば、`:JudgeIsItTrue`を指定することで、期待される変数（この場合は`it`）としてステートメントを提供できます。モデルがステートメントを「unknown」として正しく分類することに注意してください。

```julia
aiclassify(:JudgeIsItTrue; it = "Is two plus three a vegetable on Mars?") # unknown
```

より良い結果を得るために、gpt4のような高品質のモデルを使用してください。例えば、

```julia
aiclassify(:JudgeIsItTrue;
    it = "If I had two apples and I got three more, I have five apples now.",
    model = "gpt4") # true
```
