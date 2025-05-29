```
getresponse( chat::Chat
           , maxrequests::Int=1
           , compact::Bool=true
           , model::AbstractString="gpt-3.5-turbo"
           , options...)::Resp
```

OpenAI APIからの応答を取得します。

# 引数

  * `chat::Chat`: チャットログ。
  * `maxrequests::Int`: OpenAI APIへの最大リクエスト数。
  * `compact::Bool`: 応答をコンパクトにするかどうか。
  * `model::AbstractString`: 使用するモデル。
  * `**options`: `ChatAPICall.request`に渡すその他のオプション。
