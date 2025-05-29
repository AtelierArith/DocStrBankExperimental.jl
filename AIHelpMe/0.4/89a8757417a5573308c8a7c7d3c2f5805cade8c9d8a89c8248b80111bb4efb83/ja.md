```
aihelp([cfg::RT.AbstractRAGConfig, index::RT.AbstractChunkIndex,]
    question::AbstractString;
    verbose::Integer = 1,
    model = MODEL_CHAT,
    return_all::Bool = false)
```

与えられた質問に対して、Juliaのドキュメント（または他の知識パック）を使用したRetrieval-Augmented Generation (RAG)アプローチで応答を生成します。

RAGResultを返す場合（`return_all=true`）、`AIHelpMe.pprint`を使用して結果を整形表示し、回答の各チャンクのソース/"サポート"スコアを確認できます。

回答は読み込まれた知識パックに依存します。`?load_index!`を参照してください。

また、読み込んだパッケージからドキュメント文字列を追加することもできます（またはすべてのパッケージから）、`?update_index`を参照し、新しく更新されたインデックスを明示的に提供してください！

# 引数

  * `cfg::AbstractRAGConfig`: RAGの設定。
  * `index::AbstractChunkIndex`: チャンクインデックス（チャンク化され、埋め込まれたドキュメントを含む）。
  * `question::AbstractString`: 答えられる質問。
  * `model::String`: 最終応答を生成するために使用されるチャット/生成モデル、デフォルトは`MODEL_CHAT`。
  * `return_all::Bool`: `true`の場合、`RAGResult`を返します（パイプラインの詳細を提供し、`pprint(result)`で整形表示を可能にします）。
  * `search::Union{Nothing, Bool}`: `true`の場合、TavilySearchRefinerを使用してウェブ検索結果をコンテキストに追加します。詳細は`?PromptingTools.Experimental.RAGTools.TavilySearchRefiner`を参照してください。
  * `rerank::Union{Nothing, Bool}`: `true`の場合、CohereRerankerを使用してチャンクの再ランク付けを行います。詳細は`?PromptingTools.Experimental.RAGTools.CohereReranker`を参照してください。

# 戻り値

  * `return_all`が`false`の場合、生成されたメッセージ（`msg`）を返します。
  * `return_all`が`true`の場合、`RAGResult`を返します（パイプラインの詳細を提供し、`pprint(result)`で整形表示を可能にします）。

# 注意事項

  * 関数は常に、`return_all`の値に関係なく、ソース/コンテキストの検査のためにグローバル`LAST_RESULT`に最後のコンテキストを保存します。

# 例

`aihelp`を使用して質問に対する応答を取得する：

```julia
using AIHelpMe: build_index

index = build_index(...)  # Makie.jlのドキュメント（または読み込んだパッケージ）を含むインデックスを作成します

question = "Makie.jlで棒グラフを作成するには？"
msg = aihelp(index, question)
```

ソースを強調表示した整形表示の回答が必要な場合は、`return_all`引数と`pprint`ユーティリティを使用できます：

```julia
using AIHelpMe: pprint

result = aihelp(index, question; return_all = true)
pprint(result)
```

知識パックを読み込んでいる場合、インデックスを提供する必要はありません。

```julia
# Makieの知識パックを読み込む
AIHelpMe.load_index!(:makie)

question = "Makie.jlで棒グラフを作成するには？"
msg = aihelp(question)
```

難しい質問であることがわかっている場合は、`search`および`rerank`引数を使用してウェブ検索結果をコンテキストに追加し、チャンクの再ランク付けを行うことができます。

```julia
using AIHelpMe: pprint

question = "Makie.jlで棒グラフを作成するには？"
result = aihelp(question; search = true, rerank = true, return_all = true)
pprint(result) # 各チャンク/文のソースを含む整形表示（角括弧を探してください）
```
