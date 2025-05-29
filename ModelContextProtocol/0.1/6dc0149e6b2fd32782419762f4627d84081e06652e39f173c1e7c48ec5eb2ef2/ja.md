```
MCPPrompt(name::String, description::String, arguments::Vector{PromptArgument}, text::String) -> MCPPrompt
```

単一のテキストメッセージを持つプロンプトを作成します。

# 引数

  * `name::String`: プロンプトの一意の識別子
  * `description::String`: 人間が読める説明
  * `arguments::Vector{PromptArgument}`: プロンプトが受け入れる引数
  * `text::String`: プロンプトメッセージのテキストコンテンツ

# 戻り値

  * `MCPPrompt`: テキストを含む単一のユーザーメッセージを持つ新しいプロンプト
