```
UserMessageWithImages
```

ユーザー生成のテキストベースの応答と画像のためのメッセージタイプ。応答を生成するために `ai*` 関数によって消費されます。

# フィールド

  * `content::T`: メッセージの内容。
  * `image_url::Vector{String}`: 画像のURL。
  * `variables::Vector{Symbol}`: メッセージ内の変数。
  * `name::Union{Nothing, String}`: 会話内の `role` の名前。
