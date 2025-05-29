```
UserMessage
```

ユーザー生成のテキストベースの応答のためのメッセージタイプ。応答を生成するために `ai*` 関数によって使用されます。

# フィールド

  * `content::T`: メッセージの内容。
  * `variables::Vector{Symbol}`: メッセージ内の変数。
  * `name::Union{Nothing, String}`: 会話における `role` の名前。
