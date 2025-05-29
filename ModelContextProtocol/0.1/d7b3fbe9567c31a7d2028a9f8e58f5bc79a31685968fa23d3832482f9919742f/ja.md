```
MCPPrompt(; name::String, description::String="", 
        arguments::Vector{PromptArgument}=PromptArgument[], 
        messages::Vector{PromptMessage}=PromptMessage[])
```

MCPスキーマで定義されたプロンプトまたはプロンプトテンプレートを実装します。プロンプトには、取得時に引数で置き換えられる変数を含めることができます。

# フィールド

  * `name::String`: プロンプトの一意の識別子
  * `description::String`: プロンプトの目的に関する人間が読める説明
  * `arguments::Vector{PromptArgument}`: このプロンプトが受け入れる引数
  * `messages::Vector{PromptMessage}`: プロンプト内のメッセージのシーケンス
