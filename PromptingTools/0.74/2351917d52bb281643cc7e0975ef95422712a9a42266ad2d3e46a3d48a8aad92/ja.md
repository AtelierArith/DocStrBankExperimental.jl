```
create_template(; user::AbstractString, system::AbstractString="役に立つAIアシスタントとして行動します。", 
    load_as::Union{Nothing, Symbol, AbstractString} = nothing)

create_template(system::AbstractString, user::AbstractString, 
    load_as::Union{Nothing, Symbol, AbstractString} = nothing)
```

ユーザーとシステムメッセージを持つシンプルなテンプレートを作成します。`[PT.UserMessage(...), ...]`を書くのを防ぐための便利な関数です。

# 引数

  * `system::AbstractString`: システムメッセージ。通常、性格、スタイル、指示、出力形式などを定義します。
  * `user::AbstractString`: ユーザーメッセージ。通常、入力、クエリ、リクエストなどを定義します。
  * `load_as::Union{Nothing, Symbol, AbstractString}`: 提供された場合、指定された名前 `load_as` の下で `TEMPLATE_STORE` にテンプレートをロードします。`nothing` の場合、テンプレートはロードされません。

ダブルハンドルバープレースホルダー（例: `{{name}}`）を使用して、AI呼び出し中に `kwargs` によって置き換えられる変数を定義します（例を参照）。

`SystemMessage` と `UserMessage` オブジェクトのベクターを返します。`load_as` が提供されている場合、テンプレートは `TEMPLATE_STORE` と `TEMPLATE_METADATA` に登録されます。

# 例

シンプルな会話のためのクイックテンプレートを生成しましょう（プレースホルダーは1つだけ: 名前）

```julia
# 最初にシステムメッセージ、その後にユーザーメッセージ（または kwargs を使用）
tpl=PT.create_template("海賊のように話さなければなりません", "{{name}}に挨拶してください")

## 2-element Vector{PromptingTools.AbstractChatMessage}:
## PromptingTools.SystemMessage("海賊のように話さなければなりません")
##  PromptingTools.UserMessage("{{name}}に挨拶してください")
```

このテンプレートを `ai*` 関数ですぐに使用できます：

```julia
aigenerate(tpl; name="ジャック・スパロウ")
# 出力: AIMessage("アー、仲間よ！塩辛い海でキャプテン・ジャック・スパロウによろしく伝えてくれ！彼のコンパスが常に最寄りの宝物に真っ直ぐ指し示しますように。ヤー！")
```

テンプレートをテンプレートレジストリに保存したい場合は、これらの例の最後にジャンプしてください！

プロジェクトフォルダに保存したい場合：

```julia
PT.save_template("templates/GreatingPirate.json", tpl; version="1.0") # 任意で、説明を追加
```

それは保存され、ベース名、つまり `GreatingPirate` の下でアクセスされます。

他のテンプレートと同様にロードできます（テンプレートディレクトリを提供）：

```julia
PT.load_templates!("templates") # 最初の実行後にフォルダを記憶します
# 注意: 再度保存したり上書きしたりする場合、すべてのテンプレートを明示的に再ロードする必要があります！
```

「海賊」を検索してテンプレートがロードされていることを確認できます：

```julia
aitemplates("海賊")

## 1-element Vector{AITemplateMetadata}:
## PromptingTools.AITemplateMetadata
##   name: Symbol GreatingPirate
##   description: String ""
##   version: String "1.0"
##   wordcount: Int64 46
##   variables: Array{Symbol}((1,))
##   system_preview: String "海賊のように話さなければなりません"
##   user_preview: String "{{name}}に挨拶してください"
##   source: String ""
```

他のテンプレートと同様に使用できます（これはシンボルであることに注意してください、つまり `:GreatingPirate`）：

```julia
aigenerate(:GreatingPirate; name="ジャック・スパロウ")
# 出力: AIMessage("アー、仲間よ！塩辛い海でキャプテン・ジャック・スパロウによろしく伝えてくれ！彼のコンパスが常に最寄りの宝物に真っ直ぐ指し示しますように。ヤー！")
```

このテンプレートをファイルとして保存する必要がない場合でも、すべての `ai*` 関数でアクセス可能にしたい場合は、`load_as` (= テンプレート名) キーワード引数を使用できます：

```julia
# これはテンプレートを作成するだけでなく、即座に使用するために登録します
tpl=PT.create_template("海賊のように話さなければなりません", "{{name}}に挨拶してください"; load_as="GreatingPirate")

# これで他のテンプレートのように使用できます
aiextract(:GreatingPirate; name="ジャック・スパロウ")
```
