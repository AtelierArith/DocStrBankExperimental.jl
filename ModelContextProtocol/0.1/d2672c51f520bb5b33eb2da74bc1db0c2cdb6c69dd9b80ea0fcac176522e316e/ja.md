```
PromptMessage(content::Union{TextContent, ImageContent, EmbeddedResource}) -> PromptMessage
```

コンテンツのみを持つプロンプトメッセージを作成します（役割はデフォルトでユーザー）。

# 引数

  * `content::Union{TextContent, ImageContent, EmbeddedResource}`: メッセージのコンテンツ

# 戻り値

  * `PromptMessage`: デフォルトのユーザー役割を持つ新しいプロンプトメッセージ
