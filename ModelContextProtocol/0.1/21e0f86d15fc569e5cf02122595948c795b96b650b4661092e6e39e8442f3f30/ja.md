```
PromptMessage(; content::Union{TextContent, ImageContent, EmbeddedResource}, role::Role=user)
```

プロンプトテンプレート内の単一メッセージを表します。

# フィールド

  * `content::Union{TextContent, ImageContent, EmbeddedResource}`: メッセージの内容
  * `role::Role`: このメッセージがユーザーまたはアシスタントからのものであるかどうか（デフォルトはユーザー）
