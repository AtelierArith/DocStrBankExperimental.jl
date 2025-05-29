```
AITemplate
```

AITemplateは会話プロンプトのテンプレートです。このタイプは、`render`によってメッセージのセット（=プロンプト）に解決されるテンプレート名のコンテナに過ぎません。

# 命名規則

  * テンプレート名はCamelCaseであるべきです
  * 可能な限り、`<Persona>...<Variable>...`の形式に従ってください。例えば、`JudgeIsItTrue`、

      * Persona（=システムプロンプト）で始まる、例えば、`Judge` = personaは提供された情報を`judge`することを意図しています
      * コンテキストで埋めるための変数、例えば、`It` = プレースホルダー`it`
      * 変数名で終わることは役立ちます。例えば、`JuliaExpertTask`はJulia言語の専門家であることを意図し、`task`はプレースホルダー名です
  * 理想的には、テンプレート名は自己説明的であるべきです。例えば、`JudgeIsItTrue` = personaは提供された情報が真か偽かを`judge`することを意図しています

# 例

事前に作成されたテンプレートを再利用することで時間を節約し、キーワード引数でプレースホルダーを埋めるだけです：

```julia
msg = aigenerate(:JuliaExpertAsk; ask = "How do I add packages?")
```

上記は、`AITemplate`に対して明示的にディスパッチを使用するより冗長なバージョンと同等です：

```julia
msg = aigenerate(AITemplate(:JuliaExpertAsk); ask = "How do I add packages?")
```

`aitemplates`を使用して利用可能なテンプレートを見つけます：

```julia
tmps = aitemplates("JuliaExpertAsk")
# 特定のテンプレートが表示されます
# 1-element Vector{AITemplateMetadata}:
# PromptingTools.AITemplateMetadata
#   name: Symbol JuliaExpertAsk
#   description: String "For asking questions about Julia language. Placeholders: `ask`"
#   version: String "1"
#   wordcount: Int64 237
#   variables: Array{Symbol}((1,))
#   system_preview: String "You are a world-class Julia language programmer with the knowledge of the latest syntax. Your commun"
#   user_preview: String "# Question

{{ask}}"
#   source: String ""
```

上記は、テンプレートが何についてのものであるか、どのプレースホルダーが利用可能であるか、使用するのにどれくらいのコストがかかるか（=wordcount）をよく理解するのに役立ちます。

すべてのJulia関連のテンプレートを検索します：

```julia
tmps = aitemplates("Julia")
# 2-element Vector{AITemplateMetadata}... -> さらに続きます！
```

VSCodeを使用している場合、`vscodedisplay`を使用して素晴らしい表形式の表示を活用できます：

```julia
using DataFrames
tmps = aitemplates("Julia") |> DataFrame |> vscodedisplay
```

選択したテンプレートがありますが、どうやって使うのですか？最初の例で見たように、`aigenerate`または`aiclassify`で「名前」を使用するだけです！

任意のテンプレートを「レンダリング」することで検査できます（これがLLMが見るものです）：

```julia
julia> AITemplate(:JudgeIsItTrue) |> PromptingTools.render
```

詳細については、`save_template`、`load_template`、`load_templates!`を参照してください。より高度な使用例（および`examples/`フォルダー内の対応するスクリプト）があります。
