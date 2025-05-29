```
GetPromptResult(; description::String, messages::Vector{PromptMessage}) <: ResponseResult
```

プロンプトリクエストから返される結果。

# フィールド

  * `description::String`: プロンプトの説明
  * `messages::Vector{PromptMessage}`: テンプレート変数が置き換えられたプロンプトメッセージ
