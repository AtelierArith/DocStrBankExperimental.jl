```
aitemplates
```

あなたのユースケースに最も適したテンプレートを簡単に見つけることができます。

次の方法で検索できます：

  * `query::Symbol` はテンプレートの `name` で部分一致のみを探します
  * `query::AbstractString` はテンプレートの `name` または `description` で部分一致を探します
  * `query::Regex` はテンプレートの `name`、`description` またはメッセージプレビューのいずれかで一致を探します

# キーワード引数

  * `limit::Int` は返されるテンプレートの数を制限します（デフォルトは10）

# 例

`aitemplates` を使って利用可能なテンプレートを見つけます：

```julia
tmps = aitemplates("JuliaExpertAsk")
# 特定のテンプレートが表示されます
# 1-element Vector{AITemplateMetadata}:
# PromptingTools.AITemplateMetadata
#   name: Symbol JuliaExpertAsk
#   description: String "Julia言語に関する質問をするためのもの。プレースホルダー: `ask`"
#   version: String "1"
#   wordcount: Int64 237
#   variables: Array{Symbol}((1,))
#   system_preview: String "あなたは最新の構文に関する知識を持つ世界クラスのJulia言語プログラマーです。あなたのコミュ"
#   user_preview: String "# 質問

{{ask}}"
#   source: String ""
```

上記は、テンプレートが何についてのものであるか、どのプレースホルダーが利用可能であるか、使用するのにどれくらいのコストがかかるか（=wordcount）を良く理解するのに役立ちます。

Julia関連のすべてのテンプレートを検索します：

```julia
tmps = aitemplates("Julia")
# 2-element Vector{AITemplateMetadata}... -> さらに続きます！
```

VSCodeを使用している場合は、`vscodedisplay` を使って素敵な表形式の表示を活用できます：

```julia
using DataFrames
tmps = aitemplates("Julia") |> DataFrame |> vscodedisplay
```

選択したテンプレートがあるのですが、どうやって使いますか？最初の例で見たように、`aigenerate` または `aiclassify` で "name" を使うだけです！
