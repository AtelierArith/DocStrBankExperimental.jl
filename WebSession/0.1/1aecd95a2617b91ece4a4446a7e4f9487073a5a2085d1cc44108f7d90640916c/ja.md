```
get_session_data(
    key::String,
    req::HTTP.Request = Genie.Requests.request(),
    res::HTTP.Response = Genie.Responses.getresponse()
)::Union{Any, Nothing}
```

指定されたキーに一致するセッションストアのデータを取得します。

# 引数

  * `key`: 取得するデータのキー。
  * `req`: HTTP.Requestオブジェクト。デフォルトはGenie.Requests.request()です。
  * `res`: HTTP.Responseオブジェクト。デフォルトはGenie.Responses.getresponse()です。

# 戻り値

関数はデータが存在する場合はそれを返し、存在しない場合は何も返しません。
